<script setup>
import { ref } from "vue";
import HamburgerMenu from "~icons/lucide/menu";
import CloseIcon from "~icons/lucide/x";
import Button from "./Button.vue";

const props = defineProps({
  navItems: Array,
  brand: {
    type: String,
    default: "Facility Hub",
  },
});

const emit = defineEmits(["login", "signup"]);

const isMenuOpen = ref(false);
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<template>
  <header class="flex flex-col items-center justify-center" id="header">
    <div
      class="container mx-auto h-20 flex items-center justify-between px-6 md:px-8 2xl:px-0"
    >
      <!-- Logo -->
      <h1 class="text-lg font-semibold">{{ brand }}</h1>

      <!-- Desktop Nav -->
      <nav class="hidden md:flex space-x-12">
        <a
          v-for="(item, index) in navItems"
          :key="index"
          :href="item.href"
          class="hover:text-gray-400 transition-colors duration-300 rounded-full px-3 py-1"
        >
          {{ item.label }}
        </a>
      </nav>

      <!-- Desktop Actions -->
      <div class="hidden md:flex gap-4">
        <Button
          type="secondary"
          :customClasses="'border border-gray-300 hover:bg-green-50/50 rounded-full'"
          @click="$emit('login')"
        >
          Login
        </Button>
        <Button
          type="primary"
          :customClasses="'hover:bg-green-600 rounded-full'"
          @click="$emit('signup')"
        >
          Sign Up
        </Button>
      </div>

      <!-- Mobile Toggle -->
      <div class="md:hidden">
        <HamburgerMenu
          v-if="!isMenuOpen"
          @click="toggleMenu"
          class="text-2xl cursor-pointer"
        />
        <CloseIcon v-else @click="toggleMenu" class="text-2xl cursor-pointer" />
      </div>
    </div>

    <!-- Mobile Menu -->
    <div
      v-if="isMenuOpen"
      class="w-full bg-white shadow-md z-50 flex flex-col items-center md:hidden p-6"
    >
      <nav class="flex flex-col space-y-4">
        <a
          v-for="(item, index) in navItems"
          :key="index"
          :href="item.href"
          class="text-xl text-center hover:text-gray-400 transition-colors duration-300"
        >
          {{ item.label }}
        </a>
      </nav>

      <div class="w-full mt-8 flex flex-col space-y-4">
        <Button
          type="secondary"
          class="w-full border border-gray-300 rounded-md"
          @click="$emit('login')"
        >
          Login
        </Button>
        <Button
          type="primary"
          class="w-full hover:bg-green-600 rounded-md"
          @click="$emit('signup')"
        >
          Sign Up
        </Button>
      </div>
    </div>
  </header>
</template>
