<script setup lang="ts">
import { defineProps } from "vue";

interface Breadcrumb {
  name: string;
  href?: string;
  icon?: string;
}

const props = defineProps<{
  title: string;
  items: Breadcrumb[];
}>();
</script>

<template>
  <div class="w-full">
    <h1 class="text-zinc-800 text-4xl font-bold">{{ props.title }}</h1>
    <div class="mt-2 text-zinc-500 flex gap-x-2 items-center">
      <div
        v-for="(item, index) in props.items"
        :key="index"
        class="flex items-center"
      >
        <Icon v-if="item.icon" :name="item.icon" class="text-2xl mr-2" />
        <NuxtLink :to="item.href" class="text-base font-normal">
          {{ item.name }}
        </NuxtLink>
        <Icon
          v-if="index < props.items.length - 1"
          name="material-symbols:keyboard-arrow-down-rounded"
          class="-rotate-90 text-xl ml-[10px] mr-[5px]"
        />
      </div>
    </div>
  </div>
</template>
