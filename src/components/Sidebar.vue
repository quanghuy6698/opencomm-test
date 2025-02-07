<script setup lang="ts">
import { ref } from "vue";

import SearchIcon from "/src/assets/icons/search.svg";
import HomeIcon from "/src/assets/icons/home.svg";
import CheckedIcon from "/src/assets/icons/checked.svg";
import BoardIcon from "/src/assets/icons/board.svg";
import SettingsIcon from "/src/assets/icons/settings.svg";
import HelpIcon from "/src/assets/icons/help.svg";
import NotificationIcon from "/src/assets/icons/notification.svg";
import UserIcon from "/src/assets/icons/user.svg";

const topMenu = ref([
  { name: "Search", icon: SearchIcon, route: "/search" },
  { name: "Home", icon: HomeIcon, route: "/home" },
  { name: "Tasks", icon: CheckedIcon, route: "/tasks" },
  { name: "Boards", icon: BoardIcon, route: "/board" },
  { name: "Workspace settings", icon: SettingsIcon, route: "/settings" },
]);

const bottomMenu = ref([
  { name: "Help & Support", icon: HelpIcon, route: "/help" },
  { name: "Notifications", icon: NotificationIcon, route: "/notifications" },
  { name: "Profile", icon: UserIcon, route: "/profile" },
]);
</script>

<template>
  <div class="w-64 h-screen bg-gray-100 p-2 flex flex-col">
    <!-- Logo & Dropdown -->
    <div class="flex justify-between items-center">
      <div class="flex items-center">
        <img src="/src/assets/leanbase.svg" class="w-8 h-8" alt="Logo" />
        <span class="text-lg font-semibold px-2">LeanBase</span>
        <img src="/src/assets/icons/chevron-down.svg" class="w-5 h-5" alt="Logo" />
      </div>

      <img src="/src/assets/icons/aside.svg" class="w-6 h-6" alt="Collapse/Expand" />
    </div>

    <!-- Menu Items -->
    <nav class="flex-1">
      <router-link
        v-for="item in topMenu"
        :key="item.name"
        :to="item.route"
        class="flex items-center space-x-2 p-2 rounded-lg hover:bg-gray-200 transition"
      >
        <img :src="item.icon" class="w-5 h-5" :alt="item.name" />
        <span>{{ item.name }}</span>
      </router-link>
    </nav>

    <!-- Bottom Menu -->
    <div>
      <router-link
        v-for="item in bottomMenu"
        :key="item.name"
        :to="item.route"
        class="flex items-center space-x-2 p-2 rounded-lg hover:bg-gray-200 transition"
      >
        <img :src="item.icon" class="w-5 h-5" :alt="item.name" />
        <span>{{ item.name }}</span>
      </router-link>
    </div>
  </div>
</template>
