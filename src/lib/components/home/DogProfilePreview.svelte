<script>
  import { asset } from "$app/paths";
  let exampleAvatar = asset("/assets/golden-retriever-tongue-out.jpg");
  const dog = {
    name: "Biscuit McFloof",
    breed: "Golden Retriever · 3 yrs · Male",
    bio: "Professional Squirrel Chaser 🐿️ | Treat Connoisseur | Certified Zoomie Expert",
    avatarUrl: exampleAvatar,

    treats: [
      "Peanut Butter",
      "Bacon Strips",
      "Sweet Potato",
      "Blueberries",
      "Cheese",
    ],

    smells: ["Fresh Cut Grass", "BBQ Smoke", "Ocean Breeze", "Pine Trees"],

    favoritePlaces: [
      { name: "Riverside Dog Park", emoji: "🌳" },
      { name: "Main Street Café", emoji: "☕" },
      { name: "Ocean Beach Trail", emoji: "🏖️" },
      { name: "Grandma's House", emoji: "🏡" },
    ],

    dislikes: [
      "Thunderstorms",
      "The Vacuum",
      "Baths",
      "Mailman",
      "Sudden Loud Noises",
    ],

    friendlyWith: {
      dogs: true,
      cats: false,
      kids: true,
      strangers: true,
    },

    vitals: {
      weight: "68 lbs",
      energy: 4,
      trainedLevel: 3,
      barkLevel: 2,
    },

    tags: ["Neutered", "Vaccinated", "Microchipped", "Leash Trained"],
  };

  function stars(n, max = 5) {
    return Array.from({ length: max }, (_, i) => (i < n ? "●" : "○"));
  }
</script>

<section class="preview-section" id="preview">
  <div class="section-label">🐾 Example Profile</div>
  <h2 class="section-title">
    Everything Someone Needs<br />Before They Meet Your Dog
  </h2>
  <p class="section-sub">
    One link. Every detail. Zero awkward first encounters.
  </p>

  <div class="profile-card">
    <!-- Header -->
    <div class="card-header">
      <div class="avatar-ring">
        <img src={dog.avatarUrl} alt={dog.name} class="avatar" loading="lazy" />
      </div>
      <div class="card-name-group">
        <h3 class="dog-name">{dog.name}</h3>
        <p class="dog-breed">{dog.breed}</p>
        <p class="dog-bio">{dog.bio}</p>
      </div>
    </div>

    <!-- Health tags -->
    <div class="tag-row">
      {#each dog.tags as tag}
        <span class="tag">{tag}</span>
      {/each}
    </div>

    <div class="divider" aria-hidden="true"></div>

    <!-- Friendly with -->
    <div class="card-section">
      <h4 class="card-section-title">Friendly With</h4>
      <div class="friendly-grid">
        <div
          class="friendly-item"
          class:yes={dog.friendlyWith.dogs}
          class:no={!dog.friendlyWith.dogs}
        >
          <span class="friendly-icon">🐕</span>
          <span class="friendly-label">Dogs</span>
          <span class="friendly-status"
            >{dog.friendlyWith.dogs ? "✓" : "✗"}</span
          >
        </div>
        <div
          class="friendly-item"
          class:yes={dog.friendlyWith.cats}
          class:no={!dog.friendlyWith.cats}
        >
          <span class="friendly-icon">🐈</span>
          <span class="friendly-label">Cats</span>
          <span class="friendly-status"
            >{dog.friendlyWith.cats ? "✓" : "✗"}</span
          >
        </div>
        <div
          class="friendly-item"
          class:yes={dog.friendlyWith.kids}
          class:no={!dog.friendlyWith.kids}
        >
          <span class="friendly-icon">👧</span>
          <span class="friendly-label">Kids</span>
          <span class="friendly-status"
            >{dog.friendlyWith.kids ? "✓" : "✗"}</span
          >
        </div>
        <div
          class="friendly-item"
          class:yes={dog.friendlyWith.strangers}
          class:no={!dog.friendlyWith.strangers}
        >
          <span class="friendly-icon">🧑</span>
          <span class="friendly-label">Strangers</span>
          <span class="friendly-status"
            >{dog.friendlyWith.strangers ? "✓" : "✗"}</span
          >
        </div>
      </div>
    </div>

    <div class="divider" aria-hidden="true"></div>

    <!-- Vitals -->
    <div class="card-section">
      <h4 class="card-section-title">At a Glance</h4>
      <div class="vitals-grid">
        <div class="vital-row">
          <span class="vital-label">⚡ Energy Level</span>
          <span class="vital-dots">{stars(dog.vitals.energy).join(" ")}</span>
        </div>
        <div class="vital-row">
          <span class="vital-label">🎓 Training</span>
          <span class="vital-dots"
            >{stars(dog.vitals.trainedLevel).join(" ")}</span
          >
        </div>
        <div class="vital-row">
          <span class="vital-label">📢 Bark Level</span>
          <span class="vital-dots">{stars(dog.vitals.barkLevel).join(" ")}</span
          >
        </div>
        <div class="vital-row">
          <span class="vital-label">⚖️ Weight</span>
          <span class="vital-value">{dog.vitals.weight}</span>
        </div>
      </div>
    </div>

    <div class="divider" aria-hidden="true"></div>

    <!-- Fave treats -->
    <div class="card-section">
      <h4 class="card-section-title">🦴 Favourite Treats</h4>
      <div class="chip-row">
        {#each dog.treats as treat}
          <span class="chip chip-treat">{treat}</span>
        {/each}
      </div>
    </div>

    <div class="divider" aria-hidden="true"></div>

    <!-- Fave smells -->
    <div class="card-section">
      <h4 class="card-section-title">👃 Favourite Smells</h4>
      <div class="chip-row">
        {#each dog.smells as smell}
          <span class="chip chip-smell">{smell}</span>
        {/each}
      </div>
    </div>

    <div class="divider" aria-hidden="true"></div>

    <!-- Favourite places -->
    <div class="card-section">
      <h4 class="card-section-title">📍 Favourite Places</h4>
      <div class="places-list">
        {#each dog.favoritePlaces as place}
          <div class="place-row">
            <span class="place-emoji">{place.emoji}</span>
            <span class="place-name">{place.name}</span>
          </div>
        {/each}
      </div>
    </div>

    <div class="divider" aria-hidden="true"></div>

    <!-- Dislikes -->
    <div class="card-section">
      <h4 class="card-section-title">🚫 Does NOT Like</h4>
      <div class="chip-row">
        {#each dog.dislikes as dislike}
          <span class="chip chip-dislike">{dislike}</span>
        {/each}
      </div>
    </div>
  </div>
</section>

<style>
  .preview-section {
    padding: 1rem 1.5rem 2rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
  }

  .section-label {
    font-family: "Poppins", sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    color: #f4a261;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .section-title {
    font-family: "Nunito", sans-serif;
    font-size: 1.65rem;
    font-weight: 900;
    color: #4a4a4a;
    text-align: center;
    line-height: 1.2;
    margin: 0;
  }

  .section-sub {
    font-family: "Poppins", sans-serif;
    font-size: 0.82rem;
    color: #8d99ae;
    text-align: center;
    margin: 0 0 0.5rem;
  }

  /* ── Card ── */
  .profile-card {
    width: 100%;
    background: #ffffff;
    border: 1.5px solid rgba(141, 153, 174, 0.18);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 4px 32px rgba(74, 74, 74, 0.07);
  }

  .card-header {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
    padding: 1.25rem 1.25rem 1rem;
  }

  .avatar-ring {
    width: 72px;
    height: 72px;
    border-radius: 50%;
    border: 3px solid #f4a261;
    padding: 2px;
    flex-shrink: 0;
    overflow: hidden;
    box-shadow: 0 4px 14px rgba(244, 162, 97, 0.25);
  }

  .avatar {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    display: block;
  }

  .card-name-group {
    flex: 1;
    min-width: 0;
  }

  .dog-name {
    font-family: "Nunito", sans-serif;
    font-size: 1.2rem;
    font-weight: 900;
    color: #4a4a4a;
    margin: 0 0 0.1rem;
  }

  .dog-breed {
    font-family: "Poppins", sans-serif;
    font-size: 0.68rem;
    font-weight: 700;
    color: #f4a261;
    text-transform: uppercase;
    letter-spacing: 0.07em;
    margin: 0 0 0.35rem;
  }

  .dog-bio {
    font-family: "Poppins", sans-serif;
    font-size: 0.75rem;
    color: #8d99ae;
    margin: 0;
    line-height: 1.5;
  }

  /* ── Tags ── */
  .tag-row {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    padding: 0 1.25rem 1.1rem;
  }

  .tag {
    font-family: "Poppins", sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    color: #3a7d5e;
    background: rgba(74, 180, 130, 0.1);
    border: 1px solid rgba(74, 180, 130, 0.2);
    border-radius: 999px;
    padding: 0.22rem 0.65rem;
    letter-spacing: 0.02em;
  }

  /* ── Sections ── */
  .divider {
    height: 1px;
    background: rgba(141, 153, 174, 0.12);
    margin: 0 1.25rem;
  }

  .card-section {
    padding: 1rem 1.25rem;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
  }

  .card-section-title {
    font-family: "Nunito", sans-serif;
    font-size: 0.85rem;
    font-weight: 800;
    color: #4a4a4a;
    margin: 0;
  }

  /* ── Friendly grid ── */
  .friendly-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.5rem;
  }

  .friendly-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.55rem 0.75rem;
    border-radius: 10px;
    border: 1px solid transparent;
    font-family: "Poppins", sans-serif;
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

  .friendly-icon {
    font-size: 1rem;
  }
  .friendly-label {
    flex: 1;
  }
  .friendly-status {
    font-size: 0.8rem;
    font-weight: 700;
  }

  /* ── Vitals ── */
  .vitals-grid {
    display: flex;
    flex-direction: column;
    gap: 0.45rem;
  }

  .vital-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-family: "Poppins", sans-serif;
    font-size: 0.8rem;
  }

  .vital-label {
    color: #8d99ae;
  }

  .vital-dots {
    font-size: 0.65rem;
    color: #f4a261;
    letter-spacing: 0.15em;
  }

  .vital-value {
    font-weight: 700;
    color: #4a4a4a;
  }

  /* ── Chips ── */
  .chip-row {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .chip {
    font-family: "Poppins", sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    border-radius: 999px;
    padding: 0.3rem 0.75rem;
  }

  .chip-treat {
    background: rgba(244, 162, 97, 0.12);
    color: #c4722a;
    border: 1px solid rgba(244, 162, 97, 0.25);
  }

  .chip-smell {
    background: rgba(141, 153, 174, 0.1);
    color: #5a6578;
    border: 1px solid rgba(141, 153, 174, 0.22);
  }

  .chip-dislike {
    background: rgba(231, 90, 90, 0.08);
    color: #b94444;
    border: 1px solid rgba(231, 90, 90, 0.18);
  }

  /* ── Places ── */
  .places-list {
    display: flex;
    flex-direction: column;
    gap: 0.45rem;
  }

  .place-row {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    font-family: "Poppins", sans-serif;
    font-size: 0.8rem;
    color: #4a4a4a;
  }

  .place-emoji {
    font-size: 1rem;
  }
  .place-name {
    font-weight: 500;
  }
</style>
