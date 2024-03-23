<template>
  <div
    class="pt-4 border-r dark:border-zinc-600 flex flex-col flex-grow min-h-full dark:bg-zinc-900 min-w-full"
  >
    <div class="flex flex-col gap-y-3 overflow-y-auto px-4">
      <!-- Top Menu List -->
      <div v-for="menu in topMenuList" :key="menu.name" class="h-fit">
        <Button
          variant="ghost"
          size="default"
          class="text-base text-zinc-500 dark:text-zinc-400 flex justify-between items-center font-normal w-full"
          @click="toggleMenu(menu)"
        >
          <div v-if="menu.children" class="flex items-center">
            <Icon class="text-2xl mr-4" :name="menu.icon" />{{ menu.name }}
          </div>
          <NuxtLink v-else :to="menu.url" class="flex items-center w-full">
            <Icon class="text-2xl mr-4" :name="menu.icon" />{{ menu.name }}
          </NuxtLink>
          <Icon
            v-if="menu.children"
            class="transition-transform"
            :name="
              menu.expanded
                ? 'material-symbols:keyboard-arrow-up-rounded'
                : 'material-symbols:keyboard-arrow-down-rounded'
            "
          />
        </Button>
        <div v-if="menu.children && menu.expanded" class="ml-4">
          <div v-for="child in menu.children" :key="child.name" class="mt-2">
            <NuxtLink
              :to="child.url"
              class="flex items-center pl-8 py-2 text-zinc-500 w-full"
            >
              {{ child.name }}
            </NuxtLink>
          </div>
        </div>
      </div>

      <Divider class="my-3" />

      <!-- Bottom Menu List -->
      <div v-for="menu in bottomMenuList" :key="menu.name">
        <Button
          variant="ghost"
          size="default"
          class="text-base text-zinc-500 dark:text-zinc-400 flex justify-start font-normal w-full"
        >
          <NuxtLink :to="menu.url">
            <Icon class="text-2xl mr-4" :name="menu.icon" />{{ menu.name }}
          </NuxtLink>
        </Button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import DataList from "./MenuList.json";
import Divider from "../Divider.vue";

const MenuList: any[] = DataList;

const topMenuList = ref(
  MenuList.filter((menu) => menu.top).map((menu) => ({
    ...menu,
    expanded: false,
  }))
);
const bottomMenuList = ref(MenuList.filter((menu) => !menu.top));

function toggleMenu(menu: any) {
  if (menu.children) {
    menu.expanded = !menu.expanded;
  }
}
</script>
