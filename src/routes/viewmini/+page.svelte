<script lang="ts">
  // ── Data (same as DogProfilePreview) ────────────────────────────────────────
    let exampleAvatar = '/assets/golden-retriever-tongue-out.jpg'
  const dog = {
    name: 'Biscuit McFloof',
    breed: 'Golden Retriever · 3 yrs · Male',
    bio: 'Professional Squirrel Chaser 🐿️ | Treat Connoisseur | Certified Zoomie Expert',
    avatarUrl: exampleAvatar,

    treats: ['Peanut Butter', 'Bacon Strips', 'Sweet Potato', 'Blueberries', 'Cheese'],
    smells: ['Fresh Cut Grass', 'BBQ Smoke', 'Ocean Breeze', 'Pine Trees'],

    favoritePlaces: [
      { name: 'Riverside Dog Park', emoji: '🌳' },
      { name: 'Main Street Café',   emoji: '☕' },
      { name: 'Ocean Beach Trail',  emoji: '🏖️' },
      { name: "Grandma's House",    emoji: '🏡' },
    ],

    dislikes: ['Thunderstorms', 'The Vacuum', 'Baths', 'Mailman', 'Sudden Loud Noises'],

    friendlyWith: { dogs: true, cats: false, kids: true, strangers: true },

    vitals: { weight: '68 lbs', energy: 4, trainedLevel: 3, barkLevel: 2 },

    tags: ['Neutered', 'Vaccinated', 'Microchipped', 'Leash Trained'],
  }

  function stars(n: number, max = 5): string {
    return Array.from({ length: max }, (_, i) => (i < n ? '●' : '○')).join(' ')
  }

  // ── Slides definition ───────────────────────────────────────────────────────
  const slides = [
    { id: 'profile',  label: 'Profile'    },
    { id: 'social',   label: 'Social'     },
    { id: 'vitals',   label: 'Vitals'     },
    { id: 'treats',   label: 'Favourites' },
    { id: 'places',   label: 'Places'     },
    { id: 'dislikes', label: 'Dislikes'   },
  ]

  const total = slides.length

  // ── Svelte 5 runes ──────────────────────────────────────────────────────────
  let current = $state(0)

  const canPrev = $derived(current > 0)
  const canNext = $derived(current < total - 1)

  function goTo(n: number) {
    current = Math.max(0, Math.min(total - 1, n))
  }
  function prev() { goTo(current - 1) }
  function next() { goTo(current + 1) }

  // ── Touch / swipe ───────────────────────────────────────────────────────────
  let touchStartX = $state(0)

  function onTouchStart(e: TouchEvent) {
    touchStartX = e.touches[0].clientX
  }
  function onTouchEnd(e: TouchEvent) {
    const dx = e.changedTouches[0].clientX - touchStartX
    if (dx > 52)  prev()
    else if (dx < -52) next()
  }

  // ── Keyboard ────────────────────────────────────────────────────────────────
  function onKeydown(e: KeyboardEvent) {
    if (e.key === 'ArrowLeft')  prev()
    if (e.key === 'ArrowRight') next()
  }
</script>

<svelte:window onkeydown={onKeydown} />

<!-- ─────────────────────────────────────────────────────────────────────────── -->
<section class="mini-section" id="preview-mini" aria-label="Dog profile card carousel">
  <!-- Carousel wrapper -->
  <div
    class="carousel-root"
    role="region"
    aria-label="Profile cards"
    ontouchstart={onTouchStart}
    ontouchend={onTouchEnd}
  >
    <!-- ── Slide track ─────────────────────────────────────────────────────── -->
    <!-- Dynamically offsets by the (width + gap) of each previous slide -->
    <div class="slide-track" style="transform: translateX(calc(-{current * 100}% - {current} * 1rem))">

      <!-- ── SLIDE 0 · Profile ─────────────────────────────────────────────── -->
      <article class="slide" aria-label="Profile">
        <div class="card profile-card">
          <div class="avatar-hero">
            <img src={dog.avatarUrl} alt={dog.name} loading="lazy" />
            <div class="avatar-overlay">
              <div class="avatar-name-badge">
                <h3 class="dog-name">{dog.name}</h3>
                <p class="dog-breed">{dog.breed}</p>
              </div>
            </div>
          </div>
          <div class="card-body">
            <p class="dog-bio">{dog.bio}</p>
            <div class="tag-row">
              {#each dog.tags as tag}
                <span class="tag">{tag}</span>
              {/each}
            </div>
          </div>
        </div>
      </article>

      <!-- ── SLIDE 1 · Social ──────────────────────────────────────────────── -->
      <article class="slide" aria-label="Social compatibility">
        <div class="card">
          <div class="slide-eyebrow">🐕 Friendly With</div>
          <h3 class="slide-title">Who Does Biscuit Get Along With?</h3>
          <div class="friendly-grid">
            {#each [
              { icon: '🐕', label: 'Dogs',      val: dog.friendlyWith.dogs      },
              { icon: '🐈', label: 'Cats',      val: dog.friendlyWith.cats      },
              { icon: '👧', label: 'Kids',      val: dog.friendlyWith.kids      },
              { icon: '🧑', label: 'Strangers', val: dog.friendlyWith.strangers },
            ] as item}
              <div class="friendly-item {item.val ? 'yes' : 'no'}">
                <span class="fi-icon">{item.icon}</span>
                <span class="fi-label">{item.label}</span>
                <span class="fi-status">{item.val ? '✓' : '✗'}</span>
              </div>
            {/each}
          </div>
        </div>
      </article>

      <!-- ── SLIDE 2 · Vitals ──────────────────────────────────────────────── -->
      <article class="slide" aria-label="Vitals">
        <div class="card">
          <div class="slide-eyebrow">⚡ At a Glance</div>
          <h3 class="slide-title">Biscuit's Personality Vitals</h3>
          <div class="vitals-col">
            <div class="vital-row">
              <span class="vital-lbl">⚡ Energy Level</span>
              <span class="vital-dots">{stars(dog.vitals.energy)}</span>
            </div>
            <div class="vital-row">
              <span class="vital-lbl">🎓 Training</span>
              <span class="vital-dots">{stars(dog.vitals.trainedLevel)}</span>
            </div>
            <div class="vital-row">
              <span class="vital-lbl">📢 Bark Level</span>
              <span class="vital-dots">{stars(dog.vitals.barkLevel)}</span>
            </div>
            <div class="divider"></div>
            <div class="vital-row">
              <span class="vital-lbl">⚖️ Weight</span>
              <span class="vital-val">{dog.vitals.weight}</span>
            </div>
          </div>
        </div>
      </article>

      <!-- ── SLIDE 3 · Favourites ──────────────────────────────────────────── -->
      <article class="slide" aria-label="Favourites">
        <div class="card">
          <div class="slide-eyebrow">🦴 Favourites</div>
          <h3 class="slide-title">What Makes Biscuit Go Wild</h3>
          <h4 class="section-sub-title">🦴 Favourite Treats</h4>
          <div class="chip-row">
            {#each dog.treats as treat}
              <span class="chip chip-treat">{treat}</span>
            {/each}
          </div>
          <div class="divider"></div>
          <h4 class="section-sub-title">👃 Favourite Smells</h4>
          <div class="chip-row">
            {#each dog.smells as smell}
              <span class="chip chip-smell">{smell}</span>
            {/each}
          </div>
        </div>
      </article>

      <!-- ── SLIDE 4 · Places ──────────────────────────────────────────────── -->
      <article class="slide" aria-label="Favourite places">
        <div class="card">
          <div class="slide-eyebrow">📍 Spots</div>
          <h3 class="slide-title">Biscuit's Favourite Places</h3>
          <div class="places-list">
            {#each dog.favoritePlaces as place}
              <div class="place-row">
                <span class="place-bubble">{place.emoji}</span>
                <span class="place-name">{place.name}</span>
              </div>
            {/each}
          </div>
        </div>
      </article>

      <!-- ── SLIDE 5 · Dislikes ────────────────────────────────────────────── -->
      <article class="slide" aria-label="Dislikes">
        <div class="card">
          <div class="slide-eyebrow">🚫 Watch Out</div>
          <h3 class="slide-title">Does NOT Like</h3>
          <p class="slide-body-sub">Keep everyone safe and stress-free — know Biscuit's triggers before you meet.</p>
          <div class="chip-row">
            {#each dog.dislikes as dislike}
              <span class="chip chip-dislike">{dislike}</span>
            {/each}
          </div>
        </div>
      </article>

    </div><!-- /slide-track -->

    <!-- ── Navigation arrows ───────────────────────────────────────────────── -->
    <button
      class="nav-arrow nav-prev"
      onclick={prev}
      disabled={!canPrev}
      aria-label="Previous card"
    >
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
        <polyline points="15 18 9 12 15 6"/>
      </svg>
    </button>

    <button
      class="nav-arrow nav-next"
      onclick={next}
      disabled={!canNext}
      aria-label="Next card"
    >
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
        <polyline points="9 18 15 12 9 6"/>
      </svg>
    </button>

  </div><!-- /carousel-root -->

  <!-- ── Footer: label · dots · counter ────────────────────────────────────── -->
  <div class="carousel-footer">
    <span class="slide-label-text">{slides[current].label}</span>

    <div class="dot-row" role="tablist" aria-label="Slide navigation">
      {#each slides as slide, i}
        <button
          class="dot {i === current ? 'active' : ''}"
          role="tab"
          aria-selected={i === current}
          aria-label={slide.label}
          onclick={() => goTo(i)}
        ></button>
      {/each}
    </div>

    <span class="slide-counter">{current + 1} / {total}</span>
  </div>

</section>

<!-- ─────────────────────────────────────────────────────────────────────────── -->
<style>
  /* ── Root ── */
  .mini-section {
    padding: 1rem 1.25rem 2rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.65rem;
  }


  /* ── Carousel ── */
  .carousel-root {
    width: 100%;
    position: relative;
    overflow: hidden;
    border-radius: 22px;
    outline: none;
  }

  .slide-track {
    display: flex;
    gap: 1rem; /* Defines the spacing between slides */
    align-items: stretch; /* Keeps slides uniformly sized in height */
    transition: transform 0.38s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform;
  }

  .slide {
    flex: 0 0 100%; /* Sizes precisely to the carousel root width */
    width: 100%;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
  }

  /* ── Card shell ── */
  .card {
    width: 100%;
    height: 100%; /* Forces the card to scale to the slide's uniform height */
    background: #ffffff;
    border: 1.5px solid rgba(141, 153, 174, 0.18);
    border-radius: 22px;
    overflow: hidden;
    box-shadow: 0 6px 36px rgba(74, 74, 74, 0.09);
    display: flex;
    flex-direction: column;
  }

  /* ── Slide 0: Profile hero ── */
  .profile-card { padding: 0; }

  .avatar-hero {
    position: relative;
    width: 100%;
    aspect-ratio: 4 / 3;
    overflow: hidden;
    flex-shrink: 0;
  }

  .avatar-hero img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .avatar-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(30, 22, 10, 0.72) 0%, transparent 55%);
    display: flex;
    align-items: flex-end;
    padding: 1.25rem 1.25rem 1.1rem;
  }

  .avatar-name-badge {
    display: flex;
    flex-direction: column;
    gap: 0.15rem;
  }

  .dog-name {
    font-family: 'Nunito', sans-serif;
    font-size: 1.5rem;
    font-weight: 900;
    color: #ffffff;
    margin: 0;
    line-height: 1.1;
    text-shadow: 0 1px 6px rgba(0, 0, 0, 0.25);
  }

  .dog-breed {
    font-family: 'Poppins', sans-serif;
    font-size: 0.68rem;
    font-weight: 700;
    color: #F4A261;
    text-transform: uppercase;
    letter-spacing: 0.07em;
    margin: 0;
  }

  .card-body {
    padding: 1.1rem 1.25rem 1.3rem;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .dog-bio {
    font-family: 'Poppins', sans-serif;
    font-size: 0.78rem;
    color: #8D99AE;
    margin: 0;
    line-height: 1.6;
  }

  /* ── Health tags ── */
  .tag-row {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .tag {
    font-family: 'Poppins', sans-serif;
    font-size: 0.63rem;
    font-weight: 600;
    color: #3a7d5e;
    background: rgba(74, 180, 130, 0.1);
    border: 1px solid rgba(74, 180, 130, 0.2);
    border-radius: 999px;
    padding: 0.22rem 0.65rem;
    letter-spacing: 0.02em;
  }

  /* ── Inner slide headers ── */
  .slide-eyebrow {
    font-family: 'Poppins', sans-serif;
    font-size: 0.65rem;
    font-weight: 700;
    color: #F4A261;
    text-transform: uppercase;
    letter-spacing: 0.09em;
    padding: 1.25rem 1.25rem 0;
  }

  .slide-title {
    font-family: 'Nunito', sans-serif;
    font-size: 1.2rem;
    font-weight: 900;
    color: #4A4A4A;
    margin: 0.2rem 0 0.85rem;
    padding: 0 1.25rem;
    line-height: 1.25;
  }

  .slide-body-sub {
    font-family: 'Poppins', sans-serif;
    font-size: 0.76rem;
    color: #8D99AE;
    padding: 0 1.25rem;
    margin: 0 0 1rem;
    line-height: 1.65;
  }

  .section-sub-title {
    font-family: 'Nunito', sans-serif;
    font-size: 0.85rem;
    font-weight: 800;
    color: #4A4A4A;
    margin: 0 0 0.45rem;
    padding: 0 1.25rem;
  }

  /* ── Divider ── */
  .divider {
    height: 1px;
    background: rgba(141, 153, 174, 0.12);
    margin: 0.9rem 1.25rem;
  }

  /* ── Friendly grid ── */
  .friendly-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.5rem;
    padding: 0 1.25rem 1.25rem;
  }

  .friendly-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.7rem 0.8rem;
    border-radius: 12px;
    border: 1px solid transparent;
    font-family: 'Poppins', sans-serif;
    font-size: 0.78rem;
    font-weight: 600;
  }

  .friendly-item.yes {
    background: rgba(74, 180, 130, 0.08);
    border-color: rgba(74, 180, 130, 0.2);
    color: #2d7a55;
  }

  .friendly-item.no {
    background: rgba(231, 90, 90, 0.07);
    border-color: rgba(231, 90, 90, 0.18);
    color: #b94444;
  }

  .fi-icon   { font-size: 1.05rem; }
  .fi-label  { flex: 1; }
  .fi-status { font-size: 0.85rem; font-weight: 700; }

  /* ── Vitals ── */
  .vitals-col {
    display: flex;
    flex-direction: column;
    gap: 0.55rem;
    padding: 0 1.25rem 1.25rem;
  }

  .vital-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-family: 'Poppins', sans-serif;
    font-size: 0.82rem;
  }

  .vital-lbl  { color: #8D99AE; }
  .vital-dots { font-size: 0.67rem; color: #F4A261; letter-spacing: 0.15em; }
  .vital-val  { font-weight: 700; color: #4A4A4A; }

  /* ── Chips ── */
  .chip-row {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    padding: 0 1.25rem 1.25rem;
  }

  .chip {
    font-family: 'Poppins', sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    border-radius: 999px;
    padding: 0.32rem 0.8rem;
  }

  .chip-treat   { background: rgba(244,162,97,0.12);  color: #c4722a; border: 1px solid rgba(244,162,97,0.25); }
  .chip-smell   { background: rgba(141,153,174,0.1);  color: #5a6578; border: 1px solid rgba(141,153,174,0.22); }
  .chip-dislike { background: rgba(231,90,90,0.08);   color: #b94444; border: 1px solid rgba(231,90,90,0.18); }

  /* ── Places ── */
  .places-list {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    padding: 0 1.25rem 1.25rem;
  }

  .place-row {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-family: 'Poppins', sans-serif;
    font-size: 0.82rem;
    color: #4A4A4A;
  }

  .place-bubble {
    width: 38px;
    height: 38px;
    border-radius: 12px;
    background: rgba(244, 162, 97, 0.1);
    border: 1px solid rgba(244, 162, 97, 0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .place-name { font-weight: 600; }

  /* ── Navigation arrows ── */
  .nav-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #ffffff;
    border: 1.5px solid rgba(141, 153, 174, 0.2);
    box-shadow: 0 3px 14px rgba(74, 74, 74, 0.12);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    color: #4A4A4A;
    transition:
      transform   0.18s cubic-bezier(0.34, 1.56, 0.64, 1),
      opacity     0.15s ease,
      box-shadow  0.15s ease,
      border-color 0.15s ease,
      color       0.15s ease;
    z-index: 2;
    padding: 0;
  }

  .nav-arrow:hover:not(:disabled) {
    transform: translateY(-50%) scale(1.1);
    box-shadow: 0 6px 20px rgba(244, 162, 97, 0.22);
    border-color: rgba(244, 162, 97, 0.4);
    color: #F4A261;
  }

  .nav-arrow:active:not(:disabled) {
    transform: translateY(-50%) scale(0.95);
  }

  .nav-arrow:disabled {
    opacity: 0.25;
    cursor: default;
    pointer-events: none;
  }

  .nav-prev { left: -16px; }
  .nav-next { right: -16px; }

  /* ── Footer ── */
  .carousel-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 0 0.25rem;
    margin-top: 0.25rem;
  }

  .slide-label-text {
    font-family: 'Poppins', sans-serif;
    font-size: 0.68rem;
    font-weight: 700;
    color: #F4A261;
    text-transform: uppercase;
    letter-spacing: 0.07em;
    min-width: 64px;
  }

  .dot-row {
    display: flex;
    gap: 0.35rem;
    align-items: center;
  }

  .dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: rgba(141, 153, 174, 0.28);
    border: none;
    padding: 0;
    cursor: pointer;
    transition: all 0.22s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  .dot.active {
    width: 20px;
    border-radius: 3px;
    background: #F4A261;
  }

  .dot:hover:not(.active) {
    background: rgba(244, 162, 97, 0.45);
    transform: scale(1.2);
  }

  .slide-counter {
    font-family: 'Poppins', sans-serif;
    font-size: 0.68rem;
    font-weight: 600;
    color: #8D99AE;
    min-width: 32px;
    text-align: right;
  }
</style>