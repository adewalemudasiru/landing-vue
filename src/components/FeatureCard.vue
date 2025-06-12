<script>
export default {
  props: {
    feature: Object,
  },
};
</script>

<template>
  <div
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
    <p class="text-lg mt-4">{{ feature.description }}</p>
    <div class="mt-2">
      <Button
        type="secondary"
        v-if="feature.comingSoon"
        class="text-xs text-green-500 border border-green-500 rounded-md !py-1 !px-2"
      >
        Coming Soon
      </Button>
    </div>
  </div>
</template>
