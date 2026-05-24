<script>
  let { name, bio, avatarUrl = '', breed = '' } = $props()

  let imgError = $state(false)

  function handleImgError() {
    imgError = true
  }
</script>

<section class="profile-hero" aria-label="Profile">
  <div class="avatar-ring">
    {#if avatarUrl && !imgError}
      <img
        class="avatar-img"
        src={avatarUrl}
        alt="{name}'s photo"
        loading="lazy"
        onerror={handleImgError}
      />
    {:else}
      <div class="avatar-placeholder" aria-hidden="true">
        <svg width="60" height="60" viewBox="0 0 60 60" fill="none">
          <ellipse cx="30" cy="36" rx="13" ry="11" fill="#F4A261" opacity="0.5"/>
          <ellipse cx="17" cy="22" rx="5" ry="6" fill="#F4A261" opacity="0.5"/>
          <ellipse cx="24" cy="17" rx="5" ry="6" fill="#F4A261" opacity="0.5"/>
          <ellipse cx="36" cy="17" rx="5" ry="6" fill="#F4A261" opacity="0.5"/>
          <ellipse cx="43" cy="22" rx="5" ry="6" fill="#F4A261" opacity="0.5"/>
        </svg>
      </div>
    {/if}
  </div>

  <div class="profile-text">
    <h1 class="profile-name">{name}</h1>
    {#if breed}
      <p class="profile-breed">{breed}</p>
    {/if}
    <p class="profile-bio">{bio}</p>
  </div>
</section>

<style>
  /* Mobile-first Styles */
  .profile-hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2.25rem 1.5rem 1.25rem;
    text-align: center;
    gap: 1rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .avatar-ring {
    width: 118px;
    height: 118px;
    border-radius: 50%;
    border: 4px solid #F4A261;
    padding: 3px;
    background: #fff;
    box-shadow:
      0 0 0 1px rgba(244,162,97,0.15),
      0 8px 28px rgba(244, 162, 97, 0.28);
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .avatar-img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    display: block;
  }

  .avatar-placeholder {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: #FFF3E8;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .profile-text {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.3rem;
  }

  .profile-name {
    font-family: 'Nunito', sans-serif;
    font-size: 2rem;
    font-weight: 900;
    color: #4A4A4A;
    margin: 0;
    line-height: 1.15;
  }

  .profile-breed {
    font-family: 'Poppins', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    color: #F4A261;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin: 0;
  }

  .profile-bio {
    font-family: 'Poppins', sans-serif;
    font-size: 0.875rem;
    color: #8D99AE;
    margin: 0.2rem 0 0;
    line-height: 1.65;
    max-width: 290px;
  }

  /* ── Laptop / Desktop Layout Enhancements ── */
  @media (min-width: 768px) {
    .profile-hero {
      flex-direction: row; /* Align Avatar and Text side-by-side */
      text-align: left;
      align-items: flex-start;
      gap: 2.5rem;
      padding: 4rem 2rem 2.5rem;
    }

    .avatar-ring {
      width: 160px; /* Slightly larger avatar for desktop */
      height: 160px;
    }

    .profile-text {
      align-items: flex-start;
      padding-top: 1rem;
    }

    .profile-name {
      font-size: 3rem; /* Larger name */
    }

    .profile-breed {
      font-size: 0.85rem;
    }

    .profile-bio {
      max-width: 550px; /* Wider bio path */
      font-size: 1rem;
    }
  }
</style>