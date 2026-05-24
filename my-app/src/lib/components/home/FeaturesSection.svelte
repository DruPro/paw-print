<script>
  const features = [
    {
      emoji: '🦴',
      title: 'Favourite Treats',
      desc: 'Let anyone know exactly what makes your dog go absolutely wild — peanut butter, bacon strips, or fancy freeze-dried salmon.',
    },
    {
      emoji: '👃',
      title: 'Favourite Smells',
      desc: 'Share the scents your pup lives for. Great for groomers, sitters, and anyone who wants to make an instant best friend.',
    },
    {
      emoji: '📍',
      title: 'Favourite Places',
      desc: 'Tag all the spots your dog loves — the dog park, the beach trail, the café with the good water bowl.',
    },
    {
      emoji: '🚫',
      title: 'Does NOT Like',
      desc: 'Keep everyone safe and stress-free. List triggers, fears, and no-go zones so meet-and-greets go smoothly.',
    },
    {
      emoji: '🐕',
      title: 'Social Compatibility',
      desc: 'Dog friendly? Cat friendly? Kid friendly? Stranger-danger or total social butterfly? Set the record straight.',
    },
    {
      emoji: '⚡',
      title: 'Personality Vitals',
      desc: 'Energy level, training, bark level, weight — everything a dog sitter, groomer, or new friend needs at a glance.',
    },
    {
      emoji: '🏥',
      title: 'Health & Status',
      desc: 'Vaccinated, neutered, microchipped, leash trained — surface the credentials that matter most.',
    },
    {
      emoji: '🌟',
      title: 'Celebrity Dog Ready',
      desc: 'Got a famous pup? PawPrint is the perfect link-in-bio for influencer dogs with an audience to impress.',
    },
  ]
</script>

<section class="features-section">
  <div class="section-label">✨ What You Can Share</div>
  <h2 class="section-title">A Full Picture,<br />Not Just a Name</h2>
  <p class="section-sub">
    Everything a stranger, sitter, vet, or fan needs before they meet your dog.
    No awkward questions. No surprise meltdowns.
  </p>

  <div class="features-grid">
    {#each features as feature}
      <div class="feature-card">
        <span class="feature-emoji" aria-hidden="true">{feature.emoji}</span>
        <h3 class="feature-title">{feature.title}</h3>
        <p class="feature-desc">{feature.desc}</p>
      </div>
    {/each}
  </div>
</section>

<style>
  .features-section {
    padding: 2rem 1.5rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
    background: rgba(244, 162, 97, 0.04);
    border-top: 1px solid rgba(244, 162, 97, 0.1);
    border-bottom: 1px solid rgba(244, 162, 97, 0.1);
  }

  .section-label {
    font-family: 'Poppins', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    color: #F4A261;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .section-title {
    font-family: 'Nunito', sans-serif;
    font-size: 1.65rem;
    font-weight: 900;
    color: #4A4A4A;
    text-align: center;
    line-height: 1.2;
    margin: 0;
  }

  .section-sub {
    font-family: 'Poppins', sans-serif;
    font-size: 0.82rem;
    color: #8D99AE;
    text-align: center;
    line-height: 1.7;
    max-width: 320px;
    margin: 0 0 0.5rem;
  }

  .features-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
    width: 100%;
  }

  .feature-card {
    background: #fff;
    border: 1.5px solid rgba(141, 153, 174, 0.15);
    border-radius: 16px;
    padding: 1.1rem 1rem;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    transition: transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.18s ease, border-color 0.18s ease;
  }

  .feature-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(244, 162, 97, 0.14);
    border-color: rgba(244, 162, 97, 0.35);
  }

  .feature-emoji {
    font-size: 1.5rem;
    line-height: 1;
  }

  .feature-title {
    font-family: 'Nunito', sans-serif;
    font-size: 0.9rem;
    font-weight: 800;
    color: #4A4A4A;
    margin: 0;
  }

  .feature-desc {
    font-family: 'Poppins', sans-serif;
    font-size: 0.72rem;
    color: #8D99AE;
    line-height: 1.6;
    margin: 0;
  }
</style>