<script>
    import { asset } from "$app/paths";

  
</script>

<section class="hero">
  <div class="hero-badge">🐾 The New Way to Introduce Your Dog</div>

  <div class="hero-logo-wrap">
    <img src={asset('/assets/pawprint-logo.png')} alt="PawPrint" class="hero-logo" />
  </div>

  <h1 class="hero-headline">
    Your Dog Deserves<br />
    <span class="accent">Their Own Page.</span>
  </h1>

  <p class="hero-sub">
    PawPrint is the link-in-bio built for dogs. Share everything anyone needs to know
    before meeting your pup — treats, quirks, fears, faves, and more.
    Perfect for the dog park, the vet, playdates, or your celebrity fur baby.
  </p>

  <div class="hero-ctas">
    <a href="#create" class="btn-primary">Create Your Dog's Profile 🐶</a>
    <a href="#preview" class="btn-ghost">See an Example ↓</a>
  </div>

  <div class="hero-social-proof">
    <div class="paw-faces">
      {#each ['🐕', '🐩', '🦮', '🐕‍🦺', '🐾'] as face}
        <span>{face}</span>
      {/each}
    </div>
    <p>Loved by <strong>10,000+ good dogs</strong> and their humans</p>
  </div>
</section>

<style>
  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 3rem 1.75rem 2.5rem;
    gap: 1.25rem;
  }

  .hero-badge {
    font-family: 'Poppins', sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    color: #F4A261;
    background: rgba(244, 162, 97, 0.1);
    border: 1px solid rgba(244, 162, 97, 0.25);
    border-radius: 999px;
    padding: 0.35rem 1rem;
    letter-spacing: 0.03em;
    text-transform: uppercase;
  }

  .hero-logo-wrap {
    width: 88px;
    height: 88px;
    border-radius: 50%;
    padding: 3px;
    box-shadow: 0 8px 32px rgba(244, 162, 97, 0.3);
    overflow: hidden;
  }

  .hero-logo {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    display: block;
  }

  .hero-headline {
    font-family: 'Nunito', sans-serif;
    font-size: 2.6rem;
    font-weight: 900;
    color: #4A4A4A;
    line-height: 1.15;
    margin: 0;
    letter-spacing: -0.02em;
  }

  .accent {
    color: #F4A261;
  }

  .hero-sub {
    font-family: 'Poppins', sans-serif;
    font-size: 0.92rem;
    color: #8D99AE;
    line-height: 1.75;
    max-width: 340px;
    margin: 0;
  }

  .hero-ctas {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    width: 100%;
    max-width: 320px;
  }

  .btn-primary {
    display: block;
    background: #F4A261;
    color: #fff;
    font-family: 'Poppins', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    padding: 1rem 1.5rem;
    border-radius: 14px;
    text-decoration: none;
    box-shadow: 0 6px 20px rgba(244, 162, 97, 0.38);
    transition: transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.18s ease, background 0.18s ease;
  }

  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 28px rgba(244, 162, 97, 0.45);
    background: #e8924f;
  }

  .btn-ghost {
    display: block;
    color: #8D99AE;
    font-family: 'Poppins', sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    text-decoration: none;
    transition: color 0.18s ease;
  }

  .btn-ghost:hover {
    color: #F4A261;
  }

  .hero-social-proof {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
  }

  .paw-faces {
    display: flex;
    gap: 0.25rem;
    font-size: 1.3rem;
  }

  .hero-social-proof p {
    font-family: 'Poppins', sans-serif;
    font-size: 0.75rem;
    color: #8D99AE;
    margin: 0;
  }

  .hero-social-proof strong {
    color: #4A4A4A;
    font-weight: 700;
  }
</style>