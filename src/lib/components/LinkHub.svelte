<script>
  import AppHeader   from '$lib/components/AppHeader.svelte'
  import ProfileHero from '$lib/components/ProfileHero.svelte'
  import LinkStack   from '$lib/components/LinkStack.svelte'
  import SocialFooter from '$lib/components/SocialFooter.svelte'
  import PawBackground from '$lib/components/PawBackground.svelte'

  // ── Profile data ─────────────────────────────────────────────
  const profile = $state({
    name:      'Biscuit McFloof',
    breed:     'Golden Retriever · 3 yrs',
    bio:       'Professional Squirrel Chaser 🐿️ | Treat Connoisseur | Certified Zoomie Expert 🎾',
    avatarUrl: 'https://images.unsplash.com/photo-1552053831-71594a27632d?w=300&h=300&fit=crop',
  })

  const links = $state([
    { label: 'Adopt a Pup Like Me 🐾',  href: 'https://petfinder.com',       icon: 'heart',    featured: true  },
    { label: 'My Doggy Blog',            href: 'https://example.com/blog',    icon: 'paw'                       },
    { label: 'Photo Gallery',            href: 'https://example.com/photos',  icon: 'camera'                    },
    { label: 'Shop My Fave Treats',      href: 'https://example.com/shop',    icon: 'cart'                      },
    { label: 'Book a Playdate',          href: 'https://example.com/play',    icon: 'calendar'                  },
    { label: 'My Website',               href: 'https://example.com',         icon: 'globe'                     },
  ])

  const socials = $state([
    { platform: 'instagram', href: 'https://instagram.com' },
    { platform: 'tiktok',    href: 'https://tiktok.com'    },
    { platform: 'youtube',   href: 'https://youtube.com'   },
  ])
</script>

<svelte:head>
  <title>{profile.name} · PawPrint</title>
  <meta name="description" content={profile.bio} />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
  <link
    href="https://fonts.googleapis.com/css2?family=Nunito:wght@700;800;900&family=Poppins:wght@400;500;600;700&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class="page-root">
  <PawBackground />

  <div class="page-scroll">
    <AppHeader />

    <main class="content-col" id="main-content">
      <ProfileHero
        name={profile.name}
        bio={profile.bio}
        avatarUrl={profile.avatarUrl}
        breed={profile.breed}
      />

      <LinkStack {links} />

      <SocialFooter {socials} />
    </main>
  </div>
</div>

<style>
  :global(*, *::before, *::after) {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  :global(html, body) {
    height: 100%;
    background: #FDFBF7;
    color: #4A4A4A;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  :global(a) { color: inherit; }

  .page-root {
    min-height: 100dvh;
    position: relative;
  }

  .page-scroll {
    position: relative;
    z-index: 1;
    min-height: 100dvh;
    display: flex;
    flex-direction: column;
  }

  .content-col {
    width: 100%;
    max-width: 480px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    flex: 1;
    padding-bottom: env(safe-area-inset-bottom, 1rem);
  }
</style>