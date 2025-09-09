<script lang="ts">
  import favicon from "$lib/assets/favicon.svg";
  import SideNav from "$lib/SideNav.svelte";

  let { children } = $props();
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<div class="container">
  <SideNav>
    <div>Side nav content</div>
  </SideNav>

  <main>
    {@render children?.()}
  </main>
</div>

<style>
  .container {
    display: flex;
    height: 100vh;
  }
</style>
