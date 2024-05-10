<script setup lang="ts">
import { onMounted } from "vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

const { isWindows, isMac, isLinux } = useDevice();

type Arch = {
  architecture: "x86" | "arm";
  platform: "Windows" | "macOS" | "Linux";
  brands: [{ brand: string; version: string }[]];
  mobile: boolean;
};

type GithubReleaseAsset = {
  name: string;
  browser_download_url: string;
};

type GithubRelease = {
  tag_name: string;
  name: string;
  assets: GithubReleaseAsset[];
};

const arch = ref<Arch>({});
const data = ref<GithubRelease>({});

const icon = computed(() => {
  switch (arch.value.platform) {
    case "Windows":
      return ["fab", "fa-windows"];
    case "macOS":
      return ["fab", "fa-apple"];
    case "Linux":
      return ["fab", "fa-linux"];
    default:
      return ["fas", "fa-download"];
  }
});

const getAsset = (
  platform: Arch["platform"],
  arch: Arch["architecture"],
): GithubReleaseAsset | null => {
  return data.value.assets?.find((asset) => {
    if (platform === "Windows") {
      return (
        asset.name.endsWith(".exe") &&
        asset.name.includes("x64") &&
        asset.name.includes("setup")
      );
    } else if (platform === "macOS") {
      switch (arch) {
        case "x86":
          return asset.name.includes("x64") && asset.name.endsWith(".dmg");
        case "arm":
          return asset.name.includes("arm64") && asset.name.endsWith(".dmg");
        default:
          return false;
      }
    } else if (platform === "Linux") {
      return asset.name.endsWith(".deb");
    }

    return false;
  });
};

const handleDownload = () => {
  const asset = getAsset(arch.value.platform, arch.value.architecture);

  if (!asset) {
    window.open(
      "https://github.com/ChxGuillaume/MQ3T/releases/latest",
      "_blank",
    );
    return;
  }

  window.location.replace(asset.browser_download_url);
};

onBeforeMount(() => {
  if (isWindows) arch.value.platform = "Windows";
  else if (isMac) arch.value.platform = "macOS";
  else if (isLinux) arch.value.platform = "Linux";
});

onMounted(async () => {
  if (isWindows) arch.value.platform = "Windows";
  else if (isMac) arch.value.platform = "macOS";
  else if (isLinux) arch.value.platform = "Linux";

  data.value = await (
    await fetch(
      "https://api.github.com/repos/ChxGuillaume/MQ3T/releases/latest",
    )
  ).json();

  const value = await navigator.userAgentData?.getHighEntropyValues([
    "architecture",
  ]);

  if (!value) return;

  arch.value = value;
});
</script>

<template>
  <button class="btn" @click="handleDownload">
    <client-only>
      <font-awesome-icon :icon="icon" />
    </client-only>
    Download
  </button>
</template>

<style scoped>
root {
  --tw-shadow-color: #000;
}

.btn {
  @apply tw-px-4 tw-py-2 tw-flex tw-items-center tw-gap-3 tw-bg-black tw-text-white dark:tw-bg-white dark:tw-text-black tw-rounded-lg tw-transition-shadow tw-shadow-accent;
}

.btn:hover {
  box-shadow: 0 0 20px 2px var(--tw-shadow-color);
}
</style>
