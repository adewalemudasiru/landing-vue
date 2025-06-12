<script setup>
//Hooks
import { ref, onMounted } from "vue";
//Components
import Button from "./components/Button.vue";
import FeaturesSection from "./components/FeaturesSection.vue";
//Assets
import heroimg from "./assets/images/heroimg.png";
import aboutimg from "./assets/images/whoweare.jpeg";
import Building from "~icons/lucide/building-2";
import Navbar from "./components/Navbar.vue";

// NavigationData
const navItems = [
  { label: "Home", href: "/" },
  { label: "Features", href: "/features" },
  { label: "Contact", href: "/contact" },
];

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

const handleLogin = () => {
  console.log("Login clicked");
};

const handleSignup = () => {
  console.log("Sign Up clicked");
};
</script>

<template>
  <div class="grid grid-rows-[auto_1fr_auto]">
    <Navbar
      :navItems="navItems"
      brand="Facility Hub"
      @login="handleLogin"
      @signup="handleSignup"
    />

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
      <FeaturesSection />
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
