<script lang="ts">
  import "@gsa-tts/graymatter-ui/styles/base/global.css";

  import DesktopSideNav from "@gsa-tts/graymatter-ui/components/DesktopSideNav.svelte";
  import LogoutIcon from "@gsa-tts/graymatter-ui/assets/images/ai-icons/main-nav/logout.svg";

  let { children } = $props();

  const apiUrl = "#";
  const chatUrl = "#";
  const consoleUrl = "#";
  const discoverUrl = "#";

  const profileMenuData = {
    userMeta: {
      initials: "HI",
    },
    menuItems: [
      {
        label: "Log out",
        icon: LogoutIcon,
        action: "logout",
      },
    ],
  };
</script>

<DesktopSideNav {apiUrl} {chatUrl} {consoleUrl} {discoverUrl} {profileMenuData}>
  {@render children?.()}
</DesktopSideNav>
