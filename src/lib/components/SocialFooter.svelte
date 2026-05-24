<script>
    import { asset } from '$app/paths';

  let { socials = [] } = $props()

  const icons = {
    instagram: {
      label: 'Instagram',
      path: 'M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z'
    },
    tiktok: {
      label: 'TikTok',
      path: 'M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-2.88 2.5 2.89 2.89 0 0 1-2.89-2.89 2.89 2.89 0 0 1 2.89-2.89c.28 0 .54.04.79.1V9.01a6.35 6.35 0 0 0-.79-.05 6.34 6.34 0 0 0-6.34 6.34 6.34 6.34 0 0 0 6.34 6.34 6.34 6.34 0 0 0 6.33-6.34V8.69a8.18 8.18 0 0 0 4.78 1.52V6.79a4.85 4.85 0 0 1-1.01-.1z'
    },
    youtube: {
      label: 'YouTube',
      path: 'M23.495 6.205a3.007 3.007 0 0 0-2.088-2.088c-1.87-.501-9.396-.501-9.396-.501s-7.507-.01-9.396.501A3.007 3.007 0 0 0 .527 6.205a31.247 31.247 0 0 0-.522 5.805 31.247 31.247 0 0 0 .522 5.783 3.007 3.007 0 0 0 2.088 2.088c1.868.502 9.396.502 9.396.502s7.506 0 9.396-.502a3.007 3.007 0 0 0 2.088-2.088 31.247 31.247 0 0 0 .5-5.783 31.247 31.247 0 0 0-.5-5.805zM9.609 15.601V8.408l6.264 3.602z'
    },
    twitter: {
      label: 'X / Twitter',
      path: 'M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.73-8.835L1.254 2.25H8.08l4.259 5.631zm-1.161 17.52h1.833L7.084 4.126H5.117z'
    },
    facebook: {
      label: 'Facebook',
      path: 'M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z'
    }
  }
</script>

<footer class="social-footer" aria-label="Social media links">
  <div class="divider">
    <span class="divider-line"></span>
    <span class="divider-paw" aria-hidden="true">🐾</span>
    <span class="divider-line"></span>
  </div>

  <div class="social-row">
    {#each socials as social (social.platform)}
      {@const icon = icons[social.platform]}
      {#if icon}
        <a
          href={social.href}
          class="social-icon"
          target="_blank"
          rel="noopener noreferrer"
          aria-label={icon.label}
        >
          <svg viewBox="0 0 24 24" width="21" height="21" fill="currentColor" aria-hidden="true">
            <path d={icon.path} />
          </svg>
        </a>
      {/if}
    {/each}
  </div>

  <div class="footer-brand">
    <img src={asset('/assets/pawprint-logo.png')} alt="" class="footer-logo" aria-hidden="true" />
    <div class="footer-brand-text">
      <span class="footer-name">PawPrint</span>
      <span class="footer-tagline">The Link in Bio Designed for Man's Best Friend</span>
    </div>
  </div>
</footer>

<style>
  .social-footer {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
    padding: 1.25rem 1.5rem 2.75rem;
  }

  .divider {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    width: 100%;
    max-width: 240px;
  }

  .divider-line {
    flex: 1;
    height: 1px;
    background: rgba(141, 153, 174, 0.2);
  }

  .divider-paw {
    font-size: 0.85rem;
    opacity: 0.5;
  }

  .social-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1.5rem;
  }

  .social-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    color: #8D99AE;
    text-decoration: none;
    transition: transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1), color 0.18s ease;
    padding: 0.3rem;
    border-radius: 50%;
  }

  .social-icon:hover,
  .social-icon:focus-visible {
    transform: scale(1.25);
    color: #F4A261;
    outline: none;
  }

  .social-icon:active {
    transform: scale(1.05);
  }

  .footer-brand {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    opacity: 0.45;
    transition: opacity 0.18s ease;
  }

  .footer-brand:hover {
    opacity: 0.7;
  }

  .footer-logo {
    width: 22px;
    height: 22px;
    border-radius: 50%;
    object-fit: cover;
  }

  .footer-brand-text {
    display: flex;
    flex-direction: column;
    line-height: 1.1;
  }

  .footer-name {
    font-family: 'Nunito', sans-serif;
    font-size: 0.75rem;
    font-weight: 900;
    color: #4A4A4A;
  }

  .footer-tagline {
    font-family: 'Poppins', sans-serif;
    font-size: 0.48rem;
    font-weight: 500;
    color: #8D99AE;
    white-space: nowrap;
  }
</style>