<script setup lang="ts">
import { ref } from "vue";
import { Popover, PopoverButton, PopoverPanel } from "@headlessui/vue";

defineProps({
  title: String,
  description: String,
  stats: Object,
  board: String,
});

const isOpen = ref(false);

const togglePopover = () => {
  isOpen.value = true;
};

const closePopover = () => {
  isOpen.value = false;
};
</script>

<template>
  <div class="bg-white p-4 rounded-lg border-1 border-gray-300 relative">
    <h3 class="font-semibold">{{ title }}</h3>
    <p class="text-sm text-gray-600">{{ description }}</p>
    <div class="flex space-x-2 mt-2">
      <span class="px-2 py-1 text-xs rounded bg-blue-100 text-blue-600">🔵 {{ stats.blue }}</span>
      <span class="px-2 py-1 text-xs rounded bg-yellow-100 text-yellow-600">🟡 {{ stats.yellow }}</span>
      <span class="px-2 py-1 text-xs rounded bg-green-100 text-green-600">🟢 {{ stats.green }}</span>
      <span class="px-2 py-1 text-xs rounded bg-orange-100 text-orange-600">🟠 {{ stats.orange }}</span>
    </div>

    <div class="grid grid-cols-[80%_20%]">
      <p class="text-sm text-gray-500 mt-2">Assign to board: {{ board }}</p>

      <Popover v-slot="{ open }" class="relative flex justify-end">
        <PopoverButton class="">
          <span>⋮</span>
        </PopoverButton>

        <transition
          enter-active-class="transition ease-out duration-200"
          enter-from-class="opacity-0 translate-y-1"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition ease-in duration-150"
          leave-from-class="opacity-100 translate-y-0"
          leave-to-class="opacity-0 translate-y-1"
        >
          <PopoverPanel v-if="isOpen" class="absolute right-0 mt-6 w-32 bg-white shadow-lg rounded-lg p-2">
            <button @click="closePopover" class="block w-full text-left px-4 py-2 hover:bg-gray-100">✏️ Edit</button>
            <button @click="closePopover" class="block w-full text-left px-4 py-2 hover:bg-gray-100">📌 Assign</button>
            <button @click="closePopover" class="block w-full text-left px-4 py-2 text-red-600 hover:bg-gray-100">
              🗑️ Delete
            </button>
          </PopoverPanel>
        </transition>
      </Popover>
    </div>
  </div>
</template>
