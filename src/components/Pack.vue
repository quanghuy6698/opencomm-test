<script setup lang="ts">
import { computed } from "vue";
import { Popover, PopoverButton, PopoverPanel } from "@headlessui/vue";

const props = withDefaults(
  defineProps<{
    title: string;
    description: string;
    stats: Record<string, any>;
    assignees?: string[];
  }>(),
  {
    assignees: () => [],
  }
);

const displayedAssignees = computed(() => {
  if (props.assignees.length == 0) return "None";

  if (props.assignees.length <= 2) return props.assignees.join(", ");

  return `${props.assignees.slice(0, 2).join(", ")} (+${props.assignees.length - 2})`;
});

const fullAssignees = computed(() => {
  return props.assignees.join(", ");
});
</script>

<template>
  <div class="bg-white p-4 rounded-lg border-1 border-gray-300 relative">
    <h3 class="font-semibold">{{ title }}</h3>
    <p class="text-sm text-gray-600">{{ description }}</p>
    <div class="flex space-x-2 pt-2 pb-4">
      <div class="flex px-2 py-1 text-xs rounded bg-blue-100 text-blue-600">
        <img src="/src/assets/icons/pack-checked.svg" class="w-4 h-4" alt="Collapse/Expand" />
        <span class="pl-1"> {{ stats.checked }}</span>
      </div>
      <div class="flex px-2 py-1 text-xs rounded bg-yellow-100 text-yellow-600">
        <img src="/src/assets/icons/pack-target.svg" class="w-4 h-4" alt="Collapse/Expand" />
        <span class="pl-1"> {{ stats.target }}</span>
      </div>
      <div class="flex px-2 py-1 text-xs rounded bg-green-100 text-green-600">
        <img src="/src/assets/icons/pack-label.svg" class="w-4 h-4" alt="Collapse/Expand" />
        <span class="pl-1"> {{ stats.labels }}</span>
      </div>
      <div class="flex px-2 py-1 text-xs rounded bg-orange-100 text-orange-600">
        <img src="/src/assets/icons/pack-power.svg" class="w-4 h-4" alt="Collapse/Expand" />
        <span class="pl-1"> {{ stats.power }}</span>
      </div>
    </div>

    <div class="grid grid-cols-[80%_20%] pt-4 border-t-2 border-gray-300">
      <Popover v-slot="{ open }" class="relative">
        <PopoverButton class="text-sm text-gray-500 mt-2 hover:underline focus:outline-none focus:ring-0">
          Assign to board: {{ displayedAssignees }}
        </PopoverButton>
        <transition
          enter-active-class="transition ease-out duration-200"
          enter-from-class="opacity-0 translate-y-1"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition ease-in duration-150"
          leave-from-class="opacity-100 translate-y-0"
          leave-to-class="opacity-0 translate-y-1"
        >
          <PopoverPanel
            class="absolute left-0 mt-2 min-w-64 bg-white border-1 border-gray-300 shadow-lg rounded-lg p-2 text-sm"
          >
            <p class="px-2 py-1 hover:bg-gray-100">{{ fullAssignees }}</p>
          </PopoverPanel>
        </transition>
      </Popover>

      <Popover v-slot="{ open }" class="relative flex justify-end">
        <PopoverButton class="p-2 focus:outline-none focus:ring-0">
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
          <PopoverPanel
            class="z-100 absolute right-0 mt-8 w-32 bg-white border-1 border-gray-300 shadow-lg rounded-lg p-2"
          >
            <button class="flex w-full text-left px-4 py-2 hover:bg-gray-100">
              <img src="/src/assets/icons/edit.svg" class="w-6 h-6" alt="Collapse/Expand" />
              <span class="pl-2 text-gray-500">Edit</span>
            </button>
            <button class="flex w-full text-left px-4 py-2 hover:bg-gray-100">
              <img src="/src/assets/icons/assign.svg" class="w-6 h-6" alt="Collapse/Expand" />
              <span class="pl-2 text-gray-500">Assign</span>
            </button>
            <button class="flex w-full text-left px-4 py-2 hover:bg-gray-100 pt-2 border-t border-gray-300">
              <img src="/src/assets/icons/delete.svg" class="w-6 h-6" alt="Collapse/Expand" />
              <span class="pl-2 text-gray-500">Delete</span>
            </button>
          </PopoverPanel>
        </transition>
      </Popover>
    </div>
  </div>
</template>
