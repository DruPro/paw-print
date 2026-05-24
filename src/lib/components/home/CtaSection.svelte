<script>
  import { asset, resolve } from "$app/paths";
</script>

<section class="cta-section" id="create">
  <div class="cta-card">
    <img
      src={asset("/assets/pawprint-logo.png")}
      alt="PawPrint"
      class="cta-logo"
    />
    <h2 class="cta-headline">Ready to Give Your Dog<br />Their Own Page?</h2>
    <p class="cta-sub">
      Free to create. Shareable anywhere. Built with love for dogs and the
      humans who adore them.
    </p>
    <a href={resolve("/view")} class="cta-btn"> Create Your PawPrint 🐾 </a>
    <p class="cta-fine">No credit card. No nonsense. Just good dogs.</p>
  </div>
</section>

<style>
  .cta-section {
    padding: 1.5rem 1.5rem 3rem;
  }

  .cta-card {
    background: #4a4a4a;
    border-radius: 22px;
    padding: 2.25rem 1.75rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .cta-card::before {
    content: "🐾";
    position: absolute;
    font-size: 8rem;
    opacity: 0.06;
    top: -1.5rem;
    right: -1.5rem;
    line-height: 1;
    pointer-events: none;
  }

  .cta-logo {
    width: 56px;
    height: 56px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid rgba(244, 162, 97, 0.5);
  }

  .cta-headline {
    font-family: "Nunito", sans-serif;
    font-size: 1.55rem;
    font-weight: 900;
    color: #fff;
    margin: 0;
    line-height: 1.2;
  }

  .cta-sub {
    font-family: "Poppins", sans-serif;
    font-size: 0.82rem;
    color: rgba(255, 255, 255, 0.6);
    line-height: 1.7;
    margin: 0;
    max-width: 280px;
  }

  .cta-btn {
    display: inline-block;
    background: #f4a261;
    color: #fff;
    font-family: "Poppins", sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    padding: 1rem 2rem;
    border-radius: 14px;
    text-decoration: none;
    box-shadow: 0 6px 20px rgba(244, 162, 97, 0.4);
    transition:
      transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1),
      box-shadow 0.18s ease;
    margin-top: 0.25rem;
  }

  .cta-btn:hover {
    transform: translateY(-3px) scale(1.02);
    box-shadow: 0 10px 28px rgba(244, 162, 97, 0.5);
  }

  .cta-fine {
    font-family: "Poppins", sans-serif;
    font-size: 0.7rem;
    color: rgba(255, 255, 255, 0.35);
    margin: 0;
  }
</style>
