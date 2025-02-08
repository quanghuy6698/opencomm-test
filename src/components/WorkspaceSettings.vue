<script setup lang="ts">
import Pack from "./Pack.vue";
</script>

<template>
  <div class="min-h-screen">
    <div class="w-full bg-white p-6">
      <h1 class="text-2xl font-semibold pb-4">Workspace Settings</h1>

      <div class="flex space-x-4 border-b border-t border-gray-300">
        <button class="flex items-center px-4 py-2 text-gray-700 border-b-2 border-transparent hover:border-gray-700">
          <img src="/src/assets/icons/general.svg" class="w-8 h-8" alt="Logo" />
          <span class="ml-2">General</span>
        </button>
        <button class="flex items-center px-4 py-2 text-gray-700 border-b-2 border-lime-200">
          <img src="/src/assets/icons/settings-packs.svg" class="w-8 h-8 text-green-300" alt="Logo" />
          <span class="ml-2">Settings Packs</span>
        </button>
      </div>

      <h2 class="text-xl font-semibold pt-4 pb-2">All setting packs</h2>
      <p class="text-gray-600 mb-4">
        Combine task types, fields, status, labels, automation together to quickly update multiple projects.
      </p>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        <div class="flex items-center justify-center bg-gray-300 p-6 rounded-lg cursor-pointer hover:bg-gray-50">
          + Create pack
        </div>

        <Pack
          title="Product development"
          description="Use this pack for product development process."
          :stats="{ checked: 4, target: 8, labels: 13, power: 3 }"
          :assignees="['Leanbase']"
        />
        <Pack
          title="Approval & Feedback demo"
          description="Use this pack for product development process."
          :stats="{ checked: 4, target: 8, labels: 13, power: 3 }"
          :assignees="['Leanbase']"
        />
        <Pack
          title="Approval & Feedback demo"
          description="Use this pack for product development process."
          :stats="{ checked: 4, target: 8, labels: 13, power: 3 }"
          :assignees="['Bamboo', 'PrintBase', 'Front-Build', 'Dpro', 'Graphic design']"
        />
      </div>
    </div>
  </div>
</template>
