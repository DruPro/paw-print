<script>
  import logo from "$lib/assets/pawprint-logo.png";
</script>

<header class="app-header">
  <div class="logo-wrap">
    <div class="logo-img-ring">
      <img src={logo} alt="PawPrint logo" class="logo-img" />
    </div>

    <div class="logo-text-group">
      <div class="logo-wordmark">
        <span class="word-paw">PAW</span><span class="dash">-</span><span
          class="word-print">PRINT</span
        >
      </div>
      <span class="logo-tagline">The Link in Bio for Man's Best Friend</span>
    </div>
  </div>
</header>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Fredoka+One&family=Poppins:wght@400;500&display=swap");

  .app-header {
    position: sticky;
    top: 0;
    z-index: 10;
    background: rgba(253, 251, 247, 0.94);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(141, 153, 174, 0.13);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0.65rem 1.5rem;
  }

  .logo-wrap {
    display: flex;
    align-items: center;
    gap: 0.7rem;
  }

  .logo-img-ring {
    width: 42px;
    height: 42px;
    border-radius: 50%;
    padding: 2px;
    box-shadow: 0 3px 12px rgba(244, 162, 97, 0.25);
    flex-shrink: 0;
    overflow: hidden;
  }

  .logo-img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    display: block;
  }

  .logo-text-group {
    display: flex;
    flex-direction: column;
    line-height: 1;
    gap: 0.18rem;
  }

  .logo-wordmark {
    display: flex;
    align-items: baseline;
    gap: 0;
    line-height: 1;
  }

  .word-paw {
    font-family: "Fredoka One", "Nunito", sans-serif;
    font-size: 1.35rem;
    font-weight: 400;
    color: #f4a261;
    letter-spacing: 0.04em;
  }

  .dash {
    font-family: "Fredoka One", "Nunito", sans-serif;
    font-size: 1.1rem;
    color: #8d99ae;
    margin: 0 0.05rem;
    opacity: 0.6;
  }

  .word-print {
    font-family: "Fredoka One", "Nunito", sans-serif;
    font-size: 1.35rem;
    font-weight: 400;
    color: #4a4a4a;
    letter-spacing: 0.04em;
  }

  .logo-tagline {
    font-family: "Poppins", sans-serif;
    font-size: 0.5rem;
    font-weight: 500;
    color: #8d99ae;
    letter-spacing: 0.04em;
    white-space: nowrap;
    text-transform: uppercase;
  }
</style>
