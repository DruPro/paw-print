<script>
  // Pure decorative — no props
</script>

<div class="paw-bg" aria-hidden="true">
  <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
    <defs>
      <pattern id="paw-tile" x="0" y="0" width="100" height="100" patternUnits="userSpaceOnUse">
        <g transform="translate(14, 12) rotate(-20) scale(0.85)">
          <ellipse cx="10" cy="14" rx="6" ry="6.5" fill="#F4A261"/>
          <ellipse cx="3.5" cy="7" rx="2.8" ry="3.2" fill="#F4A261"/>
          <ellipse cx="7.5" cy="4" rx="2.8" ry="3.2" fill="#F4A261"/>
          <ellipse cx="12.5" cy="4" rx="2.8" ry="3.2" fill="#F4A261"/>
          <ellipse cx="16.5" cy="7" rx="2.8" ry="3.2" fill="#F4A261"/>
        </g>
        <g transform="translate(60, 58) rotate(15) scale(0.7)">
          <ellipse cx="10" cy="14" rx="6" ry="6.5" fill="#F4A261"/>
          <ellipse cx="3.5" cy="7" rx="2.8" ry="3.2" fill="#F4A261"/>
          <ellipse cx="7.5" cy="4" rx="2.8" ry="3.2" fill="#F4A261"/>
          <ellipse cx="12.5" cy="4" rx="2.8" ry="3.2" fill="#F4A261"/>
          <ellipse cx="16.5" cy="7" rx="2.8" ry="3.2" fill="#F4A261"/>
        </g>
      </pattern>
    </defs>
    <rect width="100%" height="100%" fill="url(#paw-tile)" opacity="0.2"/>
  </svg>
</div>

<style>
  .paw-bg {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }

  .paw-bg svg {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
  }
</style>