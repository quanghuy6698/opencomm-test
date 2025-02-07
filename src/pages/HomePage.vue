<script setup lang="ts">
import Sidebar from "../components/Sidebar.vue";
import WorkspaceSettings from "../components/WorkspaceSettings.vue";
</script>

<template>
  <main class="flex w-full">
    <Sidebar />
    <div class="flex-1">
      <WorkspaceSettings />
    </div>
  </main>
</template>
