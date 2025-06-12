<script>
import FeatureCard from "./FeatureCard.vue";
import Settings from "~icons/lucide/settings";
import User from "~icons/lucide/users-round";
import Subscription from "~icons/lucide/gallery-vertical-end";
import Refresh from "~icons/lucide/refresh-cw";
import QrCode from "~icons/lucide/qr-code";
import Compass from "~icons/lucide/compass";

const features = [
  {
    title: "Service Management",
    description: "Easily add, update, activate, or deactivate services.",
    icon: Settings,
    color: "#ffefd4",
    comingSoon: false,
    class: "xl:col-span-2 xl:col-start-1 xl:row-start-1",
  },
  {
    title: "User Onboarding & App access",
    description: "Invite users for instant service access.",
    icon: User,
    color: "#e5e5ff",
    comingSoon: false,
    class: "xl:col-span-2 xl:col-start-3 xl:row-start-1",
  },
  {
    title: "Subscription Tracking",
    description: "Manage subscriptions and renewals.",
    icon: Subscription,
    color: "#d4e9d4",
    comingSoon: false,
    class: "xl:col-start-1 xl:row-start-2",
  },
  {
    title: "Automated Renewal Reminders",
    description: "Notify users before subscriptions expire.",
    icon: Refresh,
    color: "#f6fdcd",
    comingSoon: true,
    class: "xl:col-start-2 xl:row-start-2",
  },
  {
    title: "Quick Booking",
    description: "Scan QR codes for instant booking.",
    icon: QrCode,
    color: "#ffefd4",
    comingSoon: true,
    class: "xl:col-start-3 xl:row-start-2",
  },
  {
    title: "Centralized Management Dashboard",
    description: "Manage everything in one dashboard.",
    icon: Compass,
    color: "#f6fdcd",
    comingSoon: false,
    class: "xl:col-start-4 xl:row-start-2",
  },
];

export default {
  components: { FeatureCard },
  data() {
    return { features };
  },
};
</script>

<template>
  <section id="features">
    <div class="container mx-auto px-6 md:px-8 2xl:px-0 py-10 lg:py-20">
      <h3 class="text-3xl font-bold text-center capitalize">
        All your Facility needs in a unified solution
      </h3>
      <div
        class="grid md:grid-cols-2 xl:grid-cols-4 gap-8 mt-12"
        :style="{ gridAutoRows: 'max-content' }"
      >
        <FeatureCard
          v-for="(feature, index) in features"
          :key="index"
          :feature="feature"
        />
      </div>
    </div>
  </section>
</template>
