<script lang="ts">
  import DesktopSideNav from "@gsa-tts/graymatter-ui/components/DesktopSideNav.svelte";
  import LogoutIcon from "@gsa-tts/graymatter-ui/assets/images/ai-icons/main-nav/logout.svg";
  import SettingsIcon from "@gsa-tts/graymatter-ui/assets/images/ai-icons/main-nav/settings.svg";
  import { onMount } from "svelte";

  let { children } = $props();

  const apiUrl = "https://api.example.com";
  const chatUrl = "https://chat.example.com";
  const consoleUrl = "https://console.example.com";
  const discoverUrl = "https://discover.example.com";

  const profileMenuData = {
    userMeta: {
      initials: "HI",
    },
    menuItems: [
      {
        label: "Settings",
        icon: SettingsIcon,
        action: "settings",
      },
      {
        label: "Log out",
        icon: LogoutIcon,
        action: "logout",
      },
    ],
  };

  onMount(() => {
    window.addEventListener("profileMenuAction", (event: Event) => {
      const customEvent = event as CustomEvent;
      const { action } = customEvent.detail;

      switch (action) {
        case "logout":
          console.log("Logout action");
          break;
        case "settings":
          console.log("Settings action");
          break;
        default:
          console.warn("Unknown action", action);
      }
    });
  });
</script>

<DesktopSideNav {apiUrl} {chatUrl} {consoleUrl} {discoverUrl} {profileMenuData}>
  {@render children?.()}
</DesktopSideNav>
