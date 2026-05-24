<script>
  import PawBackground      from '$lib/components/PawBackground.svelte'
  import AppHeader          from '$lib/components/AppHeader.svelte'
  import HeroSection        from '$lib/components/home/HeroSection.svelte'
  import FeaturesSection    from '$lib/components/home/FeaturesSection.svelte'
  import DogProfilePreview  from '$lib/components/home/DogProfilePreview.svelte'
  import HowItWorksSection  from '$lib/components/home/HowItWorksSection.svelte'
  import CtaSection         from '$lib/components/home/CtaSection.svelte'
</script>

<div class="home-page">
  <PawBackground />

  <div class="home-inner">
    <AppHeader />

    <main id="main-content">
      <HeroSection />
      <FeaturesSection />
      <DogProfilePreview />
      <HowItWorksSection />
      <CtaSection />
    </main>
  </div>
</div>

<style>
  .home-page {
    position: relative;
    min-height: 100dvh;
    background: #FDFBF7;
  }

  .home-inner {
    position: relative;
    z-index: 1;
    min-height: 100dvh;
    display: flex;
    flex-direction: column;
  }

  main {
    width: 100%;
    max-width: 480px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    flex: 1;
    padding-bottom: env(safe-area-inset-bottom, 1rem);
  }
</style>