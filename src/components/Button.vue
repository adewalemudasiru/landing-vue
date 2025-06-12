<template>
  <button
    :class="[baseClasses, customClasses]"
    :style="customStyles"
    :disabled="disabled"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "primary",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    customClasses: {
      type: String,
      default: "",
    },
    customStyles: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    baseClasses() {
      return [
        "px-4 py-2 transition-colors duration-300 cursor-pointer",
        this.type === "primary"
          ? "bg-green-800 text-white hover:bg-blue-600"
          : "",
        this.type === "secondary"
          ? "bg-white text-black hover:bg-gray-600"
          : "",
        this.disabled ? "opacity-50 cursor-not-allowed" : "",
      ];
    },
  },
};
</script>
