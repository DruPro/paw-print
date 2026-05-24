<script>
  const steps = [
    {
      number: '01',
      emoji: '📝',
      title: 'Build Your Dog\'s Profile',
      desc: 'Fill in the details — treats, smells, favourite spots, what they hate, who they get along with. Takes less than 5 minutes.',
    },
    {
      number: '02',
      emoji: '🔗',
      title: 'Get Your PawPrint Link',
      desc: 'You\'ll get a unique link — perfect for your Instagram bio, TikTok, a printed QR tag on their collar, or your vet\'s records.',
    },
    {
      number: '03',
      emoji: '🐾',
      title: 'Share Before Every Meet',
      desc: 'Send it before a playdate, a grooming session, meeting the neighbours, or introducing your celebrity dog to their fans.',
    },
  ]
</script>

<section class="how-section">
  <div class="section-label">🚀 Getting Started</div>
  <h2 class="section-title">Three Steps to Your<br />Dog's Perfect First Impression</h2>

  <div class="steps-list">
    {#each steps as step, i}
      <div class="step">
        <div class="step-left">
          <div class="step-number">{step.number}</div>
          {#if i < steps.length - 1}
            <div class="step-connector" aria-hidden="true"></div>
          {/if}
        </div>
        <div class="step-body">
          <span class="step-emoji" aria-hidden="true">{step.emoji}</span>
          <h3 class="step-title">{step.title}</h3>
          <p class="step-desc">{step.desc}</p>
        </div>
      </div>
    {/each}
  </div>
</section>

<style>
  .how-section {
    padding: 2rem 1.5rem 2.25rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
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
    margin: 0 0 0.75rem;
  }

  .steps-list {
    display: flex;
    flex-direction: column;
    gap: 0;
    width: 100%;
  }

  .step {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
  }

  .step-left {
    display: flex;
    flex-direction: column;
    align-items: center;
    flex-shrink: 0;
    width: 40px;
  }

  .step-number {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #F4A261;
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-size: 0.85rem;
    font-weight: 900;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    box-shadow: 0 4px 12px rgba(244, 162, 97, 0.3);
  }

  .step-connector {
    width: 2px;
    flex: 1;
    min-height: 2rem;
    background: rgba(244, 162, 97, 0.25);
    margin: 0.3rem 0;
  }

  .step-body {
    padding-bottom: 1.75rem;
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    padding-top: 0.5rem;
  }

  .step-emoji {
    font-size: 1.3rem;
    line-height: 1;
  }

  .step-title {
    font-family: 'Nunito', sans-serif;
    font-size: 1rem;
    font-weight: 800;
    color: #4A4A4A;
    margin: 0;
  }

  .step-desc {
    font-family: 'Poppins', sans-serif;
    font-size: 0.8rem;
    color: #8D99AE;
    line-height: 1.65;
    margin: 0;
  }
</style>