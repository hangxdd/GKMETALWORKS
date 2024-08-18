<template>
  <div
    v-if="show"
    class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-75 z-50"
  >
    <div class="relative overflow-hidden scale-75 md:scale-95 rounded-lg">
      <img :src="imageSrc" class="max-w-full max-h-screen" />
    </div>
    <button
      @click="close"
      class="z-10 absolute top-4 right-6 p-0 w-12 h-12 text-[#FA5757] hover:text-white rounded-full bg-white hover:bg-[#FA5757] duration-300 flex items-center justify-center text-2xl font-bold"
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
