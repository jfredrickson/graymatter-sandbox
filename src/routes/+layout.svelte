<script lang="ts">
  import favicon from "$lib/assets/favicon.svg";
  import SideNav from "$lib/SideNav.svelte";

  let { children } = $props();
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<SideNav>
  <dev>Side nav content</dev>
</SideNav>

{@render children?.()}
