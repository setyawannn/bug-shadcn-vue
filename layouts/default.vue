<template>
  <div
    class="mx-auto w-screen h-screen flex flex-col bg-slate-50 dark:bg-slate-900"
  >
    <div
      :class="{
        hidden: isFullscreen === 'fullscreen',
        'block h-20': isFullscreen === 'minimize',
      }"
    >
      <Header :toggleSidebar="toggleSidebar" />
    </div>
    <div class="flex overflow-hidden h-full">
      <div
        :class="{
          hidden: isFullscreen === 'fullscreen',
          'block min-h-full': isFullscreen === 'minimize',
        }"
      >
        <div class="lg:hidden overflow-auto bg-white min-h-full h-full">
          <SidebarMobile
            :class="isSidebarOpen ? isSidebarOpen : 'sidebar-open'"
          />
        </div>
        <div
          class="hidden lg:block overflow-auto bg-white w-60 min-h-full h-full"
        >
          <Sidebar />
        </div>
      </div>
      <main
        class="lg:col-span-10 px-5 w-full overflow-auto min-h-full col-span-12"
        :class="{ 'py-10': isFullscreen === 'fullscreen' }"
      >
        <Button
          variant="ghost"
          @click="toggleFullscreen"
          :class="{
            'gap-2': isFullscreen === 'minimize',
            'gap-2 absolute bottom-0': isFullscreen === 'fullscreen',
          }"
        >
          <Icon
            :name="
              isFullscreen
                ? 'material-symbols:fullscreen-exit-rounded'
                : 'material-symbols:fullscreen-rounded'
            "
          />
          {{ isFullscreen == "fullscreen" ? "Minimize" : "Fullscreen" }}
        </Button>
        <slot />
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const isSidebarOpen = ref(true);

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};
const isClient = process.client;

let isFullscreenDefault = "minimize";
if (isClient) {
  isFullscreenDefault =
    localStorage.getItem("isFullscreen") === "true" ? "fullscreen" : "minimize";
}
const isFullscreen = ref(isFullscreenDefault);
const toggleFullscreen = () => {
  if (!isClient) return;

  const doc = window.document as any;
  const docEl = doc.documentElement;

  const requestFullScreen =
    docEl.requestFullscreen ||
    docEl.mozRequestFullScreen ||
    docEl.webkitRequestFullScreen ||
    docEl.msRequestFullscreen;
  const exitFullScreen =
    doc.exitFullscreen ||
    doc.mozCancelFullScreen ||
    doc.webkitExitFullscreen ||
    doc.msExitFullscreen;

  if (
    !doc.fullscreenElement &&
    !doc.mozFullScreenElement &&
    !doc.webkitFullscreenElement &&
    !doc.msFullscreenElement
  ) {
    requestFullScreen.call(docEl);
    isFullscreen.value = "fullscreen";
    localStorage.setItem("isFullscreen", "true");
  } else {
    exitFullScreen.call(doc);
    isFullscreen.value = "minimize";
    localStorage.setItem("isFullscreen", "false");
  }
};
</script>
