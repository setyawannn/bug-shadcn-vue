<template>
  <div class="w-full">
    <Breadcrumb
      title="Test Bug"
      :items="[
        {
          name: 'Dasboard',
          href: '/',
          icon: 'material-symbols:settings-rounded',
        },
        { name: 'Nothing', href: '/' },
        { name: 'Create nothing', href: '/' },
      ]"
    />
    <DefaultCard class="min-h-[78vh] flex flex-col gap-5 mt-8">
      <div class="border rounded-md">
        <div class="bg-slate-50 p-3 border-b rounded-se-md">
          <h3 class="font-semibold text-slate-700">Children</h3>
        </div>
        <div class="flex flex-col gap-5 p-6">
          <div class="border p-4 rounded-md">
            <h4 class="font-medium text-slate-700">
              Children 1 <span class="text-red-600">*</span>
            </h4>
            <div class="grid grid-cols-6 gap-5 mt-8">
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <Select>
                  <SelectTrigger>
                    <SelectValue placeholder="Select a fruit" />
                  </SelectTrigger>
                  <SelectContent>
                    <SelectGroup>
                      <SelectLabel>Fruits</SelectLabel>
                      <SelectItem value="apple"> Apple </SelectItem>
                    </SelectGroup>
                  </SelectContent>
                </Select>
              </div>
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <SelectRoot v-model="fruit">
                  <SelectTrigger
                    class="inline-flex min-w-[160px] items-center justify-between rounded px-4 py-1 text-sm font-medium bg-white border border-gray-300 shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500"
                  >
                    <SelectValue placeholder="Select a fruit..." />
                    <SelectIcon class="ml-2 h-5 w-5 text-gray-400" />
                  </SelectTrigger>

                  <SelectContent
                    class="overflow-hidden rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none mt-1 bg-white"
                  >
                    <SelectViewport class="p-2">
                      <SelectGroup>
                        <SelectItem
                          v-for="option in options"
                          :key="option"
                          :value="option"
                          class="relative select-none py-2 pl-10 pr-4 cursor-pointer hover:bg-gray-100 text-gray-700"
                        >
                          <SelectItemText>{{ option }}</SelectItemText>
                          <SelectItemIndicator
                            class="absolute left-0 inline-flex items-center justify-center w-10 h-full"
                          >
                            <SelectIcon class="h-5 w-5" />
                          </SelectItemIndicator>
                        </SelectItem>
                      </SelectGroup>
                    </SelectViewport>
                  </SelectContent>
                </SelectRoot>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="border rounded-md">
        <div class="bg-slate-50 p-3 border-b rounded-se-md">
          <h3 class="font-semibold text-slate-700">Children</h3>
        </div>
        <div class="flex flex-col gap-5 p-6">
          <div class="border p-4 rounded-md">
            <h4 class="font-medium text-slate-700">
              Children 1 <span class="text-red-600">*</span>
            </h4>
            <div class="grid grid-cols-6 gap-5 mt-8">
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <Select>
                  <SelectTrigger>
                    <SelectValue placeholder="Select a fruit" />
                  </SelectTrigger>
                  <SelectContent>
                    <SelectGroup>
                      <SelectLabel>Fruits</SelectLabel>
                      <SelectItem value="apple"> Apple </SelectItem>
                    </SelectGroup>
                  </SelectContent>
                </Select>
              </div>
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <SelectRoot v-model="fruit">
                  <SelectTrigger
                    class="inline-flex min-w-[160px] items-center justify-between rounded px-4 py-1 text-sm font-medium bg-white border border-gray-300 shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500"
                  >
                    <SelectValue placeholder="Select a fruit..." />
                    <SelectIcon class="ml-2 h-5 w-5 text-gray-400" />
                  </SelectTrigger>

                  <SelectContent
                    class="overflow-hidden rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none mt-1 bg-white"
                  >
                    <SelectViewport class="p-2">
                      <SelectGroup>
                        <SelectItem
                          v-for="option in options"
                          :key="option"
                          :value="option"
                          class="relative select-none py-2 pl-10 pr-4 cursor-pointer hover:bg-gray-100 text-gray-700"
                        >
                          <SelectItemText>{{ option }}</SelectItemText>
                          <SelectItemIndicator
                            class="absolute left-0 inline-flex items-center justify-center w-10 h-full"
                          >
                            <SelectIcon class="h-5 w-5" />
                          </SelectItemIndicator>
                        </SelectItem>
                      </SelectGroup>
                    </SelectViewport>
                  </SelectContent>
                </SelectRoot>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="border rounded-md">
        <div class="bg-slate-50 p-3 border-b rounded-se-md">
          <h3 class="font-semibold text-slate-700">Children</h3>
        </div>
        <div class="flex flex-col gap-5 p-6">
          <div class="border p-4 rounded-md">
            <h4 class="font-medium text-slate-700">
              Children 1 <span class="text-red-600">*</span>
            </h4>
            <div class="grid grid-cols-6 gap-5 mt-8">
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <Select>
                  <SelectTrigger>
                    <SelectValue placeholder="Select a fruit" />
                  </SelectTrigger>
                  <SelectContent>
                    <SelectGroup>
                      <SelectLabel>Fruits</SelectLabel>
                      <SelectItem value="apple"> Apple </SelectItem>
                    </SelectGroup>
                  </SelectContent>
                </Select>
              </div>
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <SelectRoot v-model="fruit">
                  <SelectTrigger
                    class="inline-flex min-w-[160px] items-center justify-between rounded px-4 py-1 text-sm font-medium bg-white border border-gray-300 shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500"
                  >
                    <SelectValue placeholder="Select a fruit..." />
                    <SelectIcon class="ml-2 h-5 w-5 text-gray-400" />
                  </SelectTrigger>

                  <SelectContent
                    class="overflow-hidden rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none mt-1 bg-white"
                  >
                    <SelectViewport class="p-2">
                      <SelectGroup>
                        <SelectItem
                          v-for="option in options"
                          :key="option"
                          :value="option"
                          class="relative select-none py-2 pl-10 pr-4 cursor-pointer hover:bg-gray-100 text-gray-700"
                        >
                          <SelectItemText>{{ option }}</SelectItemText>
                          <SelectItemIndicator
                            class="absolute left-0 inline-flex items-center justify-center w-10 h-full"
                          >
                            <SelectIcon class="h-5 w-5" />
                          </SelectItemIndicator>
                        </SelectItem>
                      </SelectGroup>
                    </SelectViewport>
                  </SelectContent>
                </SelectRoot>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="border rounded-md">
        <div class="bg-slate-50 p-3 border-b rounded-se-md">
          <h3 class="font-semibold text-slate-700">Children</h3>
        </div>
        <div class="flex flex-col gap-5 p-6">
          <div class="border p-4 rounded-md">
            <h4 class="font-medium text-slate-700">
              Children 1 <span class="text-red-600">*</span>
            </h4>
            <div class="grid grid-cols-6 gap-5 mt-8">
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <Select>
                  <SelectTrigger>
                    <SelectValue placeholder="Select a fruit" />
                  </SelectTrigger>
                  <SelectContent>
                    <SelectGroup>
                      <SelectLabel>Fruits</SelectLabel>
                      <SelectItem value="apple"> Apple </SelectItem>
                    </SelectGroup>
                  </SelectContent>
                </Select>
              </div>
              <div class="flex flex-col gap-2 col-span-3">
                <Label class="w-full">Dataset</Label>
                <SelectRoot v-model="fruit">
                  <SelectTrigger
                    class="inline-flex min-w-[160px] items-center justify-between rounded px-4 py-1 text-sm font-medium bg-white border border-gray-300 shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500"
                  >
                    <SelectValue placeholder="Select a fruit..." />
                    <SelectIcon class="ml-2 h-5 w-5 text-gray-400" />
                  </SelectTrigger>

                  <SelectContent
                    class="overflow-hidden rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none mt-1 bg-white"
                  >
                    <SelectViewport class="p-2">
                      <SelectGroup>
                        <SelectItem
                          v-for="option in options"
                          :key="option"
                          :value="option"
                          class="relative select-none py-2 pl-10 pr-4 cursor-pointer hover:bg-gray-100 text-gray-700"
                        >
                          <SelectItemText>{{ option }}</SelectItemText>
                          <SelectItemIndicator
                            class="absolute left-0 inline-flex items-center justify-center w-10 h-full"
                          >
                            <SelectIcon class="h-5 w-5" />
                          </SelectItemIndicator>
                        </SelectItem>
                      </SelectGroup>
                    </SelectViewport>
                  </SelectContent>
                </SelectRoot>
              </div>
            </div>
          </div>
        </div>
      </div>
    </DefaultCard>
  </div>
</template>

<script setup lang="ts">
import {
  SelectContent,
  SelectGroup,
  SelectItem,
  SelectItemIndicator,
  SelectItemText,
  SelectLabel,
  SelectPortal,
  SelectRoot,
  SelectScrollDownButton,
  SelectScrollUpButton,
  SelectSeparator,
  SelectTrigger,
  SelectValue,
  SelectViewport,
} from "radix-vue";
import Breadcrumb from "~/components/Breadcrumb.vue";

const options = ["Apple", "Banana", "Blueberry", "Grapes", "Pineapple"];
const vegetables = ["Aubergine", "Broccoli", "Carrot", "Courgette", "Leek"];

const fruit = ref();
</script>

<style scoped></style>
