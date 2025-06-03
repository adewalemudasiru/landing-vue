<script setup>
//Hooks
import { useRoute } from "vue-router";
import { ref, onMounted } from "vue";
//Components
import Button from "./components/Button.vue";
//Assets
import heroimg from "./assets/images/heroimg.png";
import aboutimg from "./assets/images/whoweare.jpeg";
import HamburgerMenu from "~icons/lucide/menu";
import Settings from "~icons/lucide/settings";
import User from "~icons/lucide/users-round";
import Subscription from "~icons/lucide/gallery-vertical-end";
import Refresh from "~icons/lucide/refresh-cw";
import QrCode from "~icons/lucide/qr-code";
import Compass from "~icons/lucide/compass";
import Building from "~icons/lucide/building-2";
import CloseIcon from "~icons/lucide/x";

// NavigationData
const navItems = [
  { label: "Home", href: "/" },
  { label: "Features", href: "/features" },
  { label: "Contact", href: "/contact" },
];

const features = [
  {
    title: "Service Management",
    description:
      "Easily add, update, activate, or deactivate services like shared workspaces, gym services, etc. and set prices—all in one place.",
    icon: Settings,
    color: "#ffefd4",
    comingSoon: false,
    class: "xl:col-span-2 xl:col-start-1 xl:row-start-1",
    // class: "col-span-4"
  },
  {
    title: "User Onboarding & App access",
    description:
      "Invite users to your facility for instant access to services and streamlined onboarding. They also get a web app for easy service access.",
    icon: User,
    color: "#e5e5ff",
    comingSoon: false,
    class: "xl:col-span-2 xl:col-start-3 xl:row-start-1",
  },
  {
    title: "Subscription Tracking",
    description:
      "Track all user subscriptions to your services, helping you manage engagement and renewals.",
    icon: Subscription,
    color: "#d4e9d4",
    comingSoon: false,
    class: "xl:col-start-1 xl:row-start-2",
  },
  {
    title: "Automated Renewal Reminders",
    description:
      "Automatic reminders notify users when subscriptions are about to expire, ensuring seamless renewals.",
    icon: Refresh,
    color: "#f6fdcd",
    comingSoon: true,
    class: "xl:col-start-2 xl:row-start-2",
  },
  {
    title: "Quick Booking",
    description:
      "Users can scan a QR code to instantly book services, making facility access fast and easy.",
    icon: QrCode,
    color: "#ffefd4",
    comingSoon: true,
    class: "xl:col-start-3 xl:row-start-2",
  },
  {
    title: "Centralized Management Dashboard",
    description:
      "Access all your management tools in one intuitive dashboard — no more juggling multiple apps.",
    icon: Compass,
    color: "#f6fdcd",
    comingSoon: false,
    class: "xl:col-start-4 xl:row-start-2",
  },
];

// Route
const route = useRoute();

//hero Data
const words = ["Facility", "Gym", "Co-workspaces", "Sport Complex"];
const currentWord = ref("");
let index = 0;

onMounted(() => {
  setInterval(() => {
    currentWord.value = words[index];
    index = (index + 1) % words.length;
  }, 1500);
});

const isMenuOpen = ref(false);
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const handleClick = () => {
  console.log("Clicked");
};
</script>

<template>
  <div class="grid grid-rows-[auto_1fr_auto]">
    <header id="header" class="flex flex-col items-center justify-center">
      <div
        class="container mx-auto h-20 flex items-center justify-between px-6 md:px-8 2xl:px-0"
      >
        <!-- Logo -->
        <h1 class="text-lg font-semibold">Facility Hub</h1>

        <!-- Desktop Navigation -->
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

        <!-- Actions (Desktop Only) -->
        <div class="hidden md:flex gap-4">
          <Button
            type="secondary"
            :customClasses="'border border-gray-300 hover:bg-green-50/50 rounded-full'"
            @click="handleClick"
          >
            Login
          </Button>
          <Button
            type="primary"
            :customClasses="'hover:bg-green-600 rounded-full'"
            @click="handleClick"
          >
            Sign Up
          </Button>
        </div>

        <!-- Hamburger Menu (Mobile Only) -->
        <div class="md:hidden">
          <HamburgerMenu
            v-if="!isMenuOpen"
            @click="toggleMenu"
            class="text-2xl cursor-pointer"
          />
          <CloseIcon
            v-else
            @click="toggleMenu"
            class="text-2xl cursor-pointer"
          />
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
            @click="handleClick"
          >
            Login
          </Button>
          <Button
            type="primary"
            class="w-full hover:bg-green-600 rounded-md"
            @click="handleClick"
          >
            Sign Up
          </Button>
        </div>
      </div>
    </header>

    <main id="main" class="min-h-screen pb-10">
      <section id="hero">
        <div
          class="container mx-auto grid grid-cols-1 md:grid-cols-2 py-10 lg:py-20 gap-8 px-6 md:px-8 2xl:px-0"
        >
          <div class="flex flex-col justify-center gap-4">
            <h2 class="flex flex-col text-4xl lg:text-7xl font-bold">
              <span>Effortless</span> <span>{{ currentWord }}</span>
              <span>Management</span>
            </h2>
            <p class="text-lg lg:text-xl">
              Manage your facilities (workspaces, gym, etc.) users,
              subscriptions, and services in one place
            </p>
            <div class="flex gap-4">
              <Button
                type="primary"
                class="border border-green-800 rounded-md"
                @click="handleClick"
                >Get Started</Button
              >
              <Button
                type="secondary"
                class="border border-green-800 rounded-md"
                @click="handleClick"
                >Book A Demo</Button
              >
            </div>
          </div>
          <div class="w-full">
            <img
              :src="heroimg"
              alt="Hero Image"
              class="w-full max-w-[800px] h-auto rounded-xl"
            />
          </div>
        </div>
      </section>
      <section id="features">
        <div class="container mx-auto px-6 md:px-8 2xl:px-0 py-10 lg:py-20">
          <h3 class="text-3xl font-bold text-center capitalize">
            All your Facility needs in a unified solution
          </h3>
          <div
            class="grid md:grid-cols-2 xl:grid-cols-4 gap-8 mt-12"
            :style="{
              gridAutoRows: 'max-content',
            }"
          >
            <div
              v-for="(feature, index) in features"
              :key="index"
              :class="feature.class"
              class="flex flex-col p-6 border border-gray-300 rounded-xl shadow-sm"
            >
              <div
                :style="{ backgroundColor: feature.color }"
                class="w-fit p-1 rounded-md"
              >
                <component :is="feature.icon" class="size-8 text-slate-600" />
              </div>

              <h4 class="text-2xl font-bold mt-8">{{ feature.title }}</h4>
              <p class="text-lg mt-4">
                {{ feature.description }}
              </p>
              <div class="mt-2">
                <Button
                  type="secondary"
                  v-if="feature.comingSoon"
                  class="text-xs text-green-500 border border-green-500 rounded-md !py-1 !px-2"
                  >Coming Soon</Button
                >
              </div>
            </div>
          </div>
        </div>
      </section>
      <section id="banner">
        <div class="w-full bg-gradient-to-r from-[#f0ff00] to-[#59cffa]">
          <div
            class="container mx-auto flex flex-col items-center text-center space-y-5 text-black rounded-lg px-6 md:px-8 2xl:px-0 py-10 lg:py-20"
          >
            <h3 class="text-3xl lg:text-4xl font-bold">
              Revolutionize Your Facility Experience with Satisfaction
            </h3>
            <p class="text-lg">
              Facility Hub provides the tools you need to manage and connect
              your spaces efficiently. Schedule a demo to learn more.
            </p>
            <Button
              type="secondary"
              class="border border-black !bg-black text-white rounded-md"
              @click="handleClick"
              >Book A Demo</Button
            >
          </div>
        </div>
      </section>
      <section id="about">
        <div class="container mx-auto px-6 md:px-8 2xl:px-0 py-10 lg:py-20">
          <h2 class="text-4xl lg:text-7xl font-bold text-center capitalize">
            Who we are
          </h2>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8">
            <div class="flex flex-col justify-center">
              <div
                class="w-full flex items-center justify-center md:justify-start"
              >
                <Building class="text-green-500 size-20 md:size-10" />
              </div>
              <div
                class="text-lg lg:text-xl font-medium text-slate-700 space-y-4 mt-4"
              >
                <p>
                  Facility Hub is a comprehensive platform for workspace owners
                  and users. Workspace owners can list and manage their
                  available services, invite users to join and subscribe to
                  their services, and manage subscriptions in one app.
                </p>
                <p>
                  Users benefit from a streamlined subscription experience and
                  access to personalized dashboards, making it easy to find and
                  book spaces that suit their needs.
                </p>
              </div>
            </div>
            <div class="w-full">
              <img
                :src="aboutimg"
                alt=""
                class="w-full max-h-[600px] object-cover object-top rounded-xl"
              />
            </div>
          </div>
        </div>
      </section>
      <section id="call-to-action">
        <div class="container mx-auto px-6 md:px-8 2xl:px-0">
          <div class="bg-blue-500 px-6 py-10 lg:py-20 rounded-xl">
            <h2
              class="text-3xl lg:text-4xl text-white font-bold text-center capitalize"
            >
              Start Managing Your Facilities Now
            </h2>
            <div class="flex justify-center mt-6">
              <Button
                type="secondary"
                class="border border-black !bg-black text-white text-xl font-semibold rounded-md"
                @click="handleClick"
                >Start Now</Button
              >
            </div>
          </div>
        </div>
      </section>
    </main>
    <footer id="footer" class="border-t border-gray-300">
      <div class="container mx-auto text-center py-6">
        <p class="text-base text-slate-700">
          © Copyright 2024, All Rights Reserved by FacilityHub
        </p>
      </div>
    </footer>
  </div>
</template>
