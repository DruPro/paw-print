<script>
  import LinkButton from './LinkButton.svelte'

  /**
   * @type {{
   *   links: Array<{
   *     label: string,
   *     href: string,
   *     icon?: string,
   *     featured?: boolean
   *   }>
   * }}
   */
  let { links = [] } = $props()
</script>

<section class="link-stack" aria-label="Links">
  {#each links as link (link.href)}
    <LinkButton
      label={link.label}
      href={link.href}
      icon={link.icon}
      featured={link.featured ?? false}
    />
  {/each}
</section>

<style>
  .link-stack {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    padding: 0.5rem 1.5rem 1rem;
    width: 100%;
  }
</style>