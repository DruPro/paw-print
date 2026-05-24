<script>
  let { label, href, icon = 'globe', featured = false } = $props()

  const iconPaths = {
    globe:    'M12 2a10 10 0 1 0 0 20A10 10 0 0 0 12 2zm0 2c.55 0 1.3.56 2 1.9.42.8.78 1.9 1.02 3.1H9c.24-1.2.6-2.3 1.02-3.1C10.7 4.56 11.45 4 12 4zM8.83 4.7C8.3 5.6 7.88 6.75 7.6 8H5.07A8.03 8.03 0 0 1 8.83 4.7zM4.58 10h2.95c-.07.64-.11 1.31-.11 2s.04 1.36.11 2H4.58A7.9 7.9 0 0 1 4 12c0-.7.21-1.37.58-2zm.5 6h2.52c.28 1.25.7 2.4 1.23 3.3A8.03 8.03 0 0 1 5.07 16zM9 16h6c-.24 1.2-.6 2.3-1.02 3.1-.7 1.34-1.45 1.9-2 1.9-.55 0-1.3-.56-2-1.9C9.58 18.3 9.22 17.2 9 16zm7 0h2.52a8.03 8.03 0 0 1-3.75 3.3c.54-.9.95-2.05 1.23-3.3zm2.95-2h-2.52c.07-.64.11-1.31.11-2s-.04-1.36-.11-2h2.95c.37.63.58 1.3.58 2s-.21 1.37-.58 2zm-3.02-6c-.28-1.25-.7-2.4-1.23-3.3A8.03 8.03 0 0 1 18.93 8h-2.52z',
    paw:      'M12 14c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4zM4 8c1.1 0 2-.9 2-2s-.9-2-2-2-2 .9-2 2 .9 2 2 2zm2.45 1.05A3.5 3.5 0 0 0 4 8.5C2.07 8.5.5 10.07.5 12S2.07 15.5 4 15.5a3.48 3.48 0 0 0 2.45-1.05zM20 8c1.1 0 2-.9 2-2s-.9-2-2-2-2 .9-2 2 .9 2 2 2zm-2.45 1.05A3.48 3.48 0 0 1 20 8.5c1.93 0 3.5 1.57 3.5 3.5s-1.57 3.5-3.5 3.5a3.48 3.48 0 0 1-2.45-1.05zM12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4z',
    camera:   'M9 3L7.17 5H4C2.9 5 2 5.9 2 7v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2h-3.17L15 3H9zm3 15c-2.76 0-5-2.24-5-5s2.24-5 5-5 5 2.24 5 5-2.24 5-5 5zm0-8c-1.65 0-3 1.35-3 3s1.35 3 3 3 3-1.35 3-3-1.35-3-3-3z',
    cart:     'M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zm10 0c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2zM7.2 14.79A1 1 0 0 0 8.1 16h9.45c.75 0 1.41-.41 1.75-1.03l3.24-5.88A1 1 0 0 0 21.66 8H5.21L4.27 4H1v2h2l3.6 7.59z',
    heart:    'M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z',
    star:     'M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z',
    video:    'M17 10.5V7c0-.55-.45-1-1-1H4c-.55 0-1 .45-1 1v10c0 .55.45 1 1 1h12c.55 0 1-.45 1-1v-3.5l4 4v-11l-4 4z',
    mail:     'M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z',
    calendar: 'M19 3h-1V1h-2v2H8V1H6v2H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H5V8h14v11z',
    bone:     'M21.07 4.93a3 3 0 0 0-4.24 0L15.66 6.1a3 3 0 0 0-4.24 4.24L9.24 12.5a3 3 0 0 0-4.24 4.24 3 3 0 0 0 4.24 0l1.17-1.17a3 3 0 0 0 4.24-4.24l2.17-2.17a3 3 0 0 0 4.24-4.24z',
  }

  const d = $derived(iconPaths[icon] ?? iconPaths.globe)
</script>

<a
  {href}
  class="link-btn"
  class:featured
  target="_blank"
  rel="noopener noreferrer"
>
  <span class="link-icon" aria-hidden="true">
    <svg width="19" height="19" viewBox="0 0 24 24" fill="currentColor">
      <path d={d} />
    </svg>
  </span>
  <span class="link-label">{label}</span>
  <span class="link-arrow" aria-hidden="true">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor">
      <path d="M7 17L17 7M17 7H7M17 7v10"/>
    </svg>
  </span>
</a>

<style>
  .link-btn {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    width: 100%;
    padding: 1rem 1.1rem;
    background: #ffffff;
    border: 1.5px solid rgba(141, 153, 174, 0.2);
    border-radius: 14px;
    text-decoration: none;
    color: #4A4A4A;
    font-family: 'Poppins', sans-serif;
    font-size: 0.88rem;
    font-weight: 600;
    cursor: pointer;
    transition:
      transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1),
      box-shadow 0.18s ease,
      background 0.18s ease,
      color 0.18s ease,
      border-color 0.18s ease;
  }

  .link-btn:hover,
  .link-btn:focus-visible {
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(244, 162, 97, 0.2);
    border-color: #F4A261;
    color: #E8864A;
    outline: none;
    background: #FFFAF5;
  }

  .link-btn:active {
    transform: translateY(-1px);
    box-shadow: 0 3px 10px rgba(244, 162, 97, 0.15);
  }

  .link-btn.featured {
    background: #F4A261;
    border-color: #F4A261;
    color: #fff;
    box-shadow: 0 4px 18px rgba(244, 162, 97, 0.38);
  }

  .link-btn.featured:hover {
    background: #e8924f;
    border-color: #e8924f;
    color: #fff;
    box-shadow: 0 10px 28px rgba(244, 162, 97, 0.45);
  }

  .link-icon {
    display: flex;
    align-items: center;
    flex-shrink: 0;
    opacity: 0.65;
    transition: opacity 0.18s ease;
  }

  .link-btn:hover .link-icon,
  .link-btn.featured .link-icon {
    opacity: 1;
  }

  .link-label {
    flex: 1;
    text-align: center;
  }

  .link-arrow {
    display: flex;
    align-items: center;
    flex-shrink: 0;
    opacity: 0;
    transform: translate(-4px, 4px);
    transition: opacity 0.18s ease, transform 0.18s ease;
  }

  .link-btn:hover .link-arrow {
    opacity: 0.5;
    transform: translate(0, 0);
  }

  .link-btn.featured .link-arrow {
    opacity: 0.6;
  }
</style>