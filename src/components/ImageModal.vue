<template>
  <div
    v-if="show"
    class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-75 z-50"
  >
    <div class="relative bg-white rounded-lg shadow-lg overflow-hidden">
      <img :src="imageSrc" class="max-w-full max-h-screen" />
    </div>
    <button
      @click="close"
      class="absolute top-4 right-6 text-white hover:text-[#FA5757] duration-300 text-5xl font-bold"
    >
      &times;
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  show: Boolean,
  imageSrc: String,
});
const emit = defineEmits(["close"]);

const close = () => {
  emit("close");
};
</script>
