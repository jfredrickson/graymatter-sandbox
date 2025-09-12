<script lang="ts">
  import favicon from "$lib/assets/favicon.svg";
  import SideNav from "$lib/SideNav.svelte";

  /**
   * Astro (which we're using for other parts of the product) has an experimental font loader
   * that handles this part. To replicate this in Sveltekit, you have to manually set up the fonts
   * and set them on the `html`.
   *
   * I installed a few dependencies.
   * 1) I'm loading the font from @fontsource so they can be installed and managed via npm.
   * 2) I get the URL for the font file so I can preload it and avoid FOUC.
   * 3) In the vite config, I added the `fontaine` plugin, which is a nice to have. It automatically
   *    matches the fallback fonts to the web font so there aren't big layout shifts
   *    when the web font loads.
   */
  import "@fontsource-variable/archivo";
  import archivoWoff2 from '@fontsource-variable/archivo/files/archivo-latin-standard-normal.woff2?url'; // Get URL for specific font file

  /**
   * This is the global CSS file that we use for the graymatter-ui library, so I moved it
   * out of the `SideNav.svelte` file and into the layout so it can be loaded for
   * all pages.
   */
  import "@gsa-tts/graymatter-ui/styles/base/global.css";

  let { children } = $props();
</script>

<svelte:head>
  <link rel="preload" as="font" href={archivoWoff2} type="font/woff2" crossorigin />
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
  :global(:root) {
    --ai-font-family-sans: 'Archivo', sans-serif;
  }

  :global(body) {
    font-family: var(--ai-font-family-sans);
  }

  .container {
    display: flex;
    height: 100vh;
  }
</style>
