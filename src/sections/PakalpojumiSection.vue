<script setup>
import pakalpojumi from "../data/pakalpojumi.js";
import { ref, computed } from "vue";
import ImageModal from "../components/ImageModal.vue";

let isOpen = ref(1);
let currentIndex = ref(0);
let showModal = ref(false);
const maxDots = 5; // Set the maximum number of visible dots

const openModal = () => {
  showModal.value = true;
};
const closeModal = () => {
  showModal.value = false;
};

const visibleDots = computed(() => {
  const images = pakalpojumi[isOpen.value - 1].details.images;
  const totalImages = images.length;

  if (totalImages <= maxDots) {
    return images.map((image, index) => ({ image, index }));
  }

  const start = Math.max(0, currentIndex.value - Math.floor(maxDots / 2));
  const end = Math.min(totalImages, start + maxDots);

  return images
    .slice(start, end)
    .map((image, index) => ({ image, index: start + index }));
});

const prevDot = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--;
  }
};

const nextDot = () => {
  const images = pakalpojumi[isOpen.value - 1].details.images;
  if (currentIndex.value < images.length - 1) {
    currentIndex.value++;
  }
};
</script>

<template>
  <!-- Pakalpojumi Section Start -->
  <div id="pakalpojumi" class="container mx-auto px-5">
    <section class="py-16">
      <div class="w-4/5 md:w-3/5 mx-auto">
        <h2 class="text-3xl md:text-4xl font-semibold font-theme-heading text-center">
          Pakalpojumi
        </h2>
        <p class="text-theme-grayish-blue text-center mt-7 font-theme-content text-lg">
          Sertificēti, profesionāli metināšanas pakalpojumi - siltumtīklu, atbildīgu
          būvkonstrukciju metināšana,montāža būvobjektos un uz vietas, metālizstrādājumu
          izgatavošana un remonts (veramie/bīdāmie vārti, balkona margas, kāpnes,
          platformas, metāla dūmvadi, visāda veida stiprinajumi, auto virsbūve, dārza
          instrumenti u.c.)
        </p>
      </div>

      <div class="mt-10">
        <ul
          class="flex flex-col items-center md:flex-row justify-center font-theme-heading"
        >
          <li
            v-for="pakalpojums in pakalpojumi"
            :key="pakalpojums.id"
            :class="
              isOpen === pakalpojums.id ? 'md:border-b-4 md:border-theme-secondary' : ''
            "
            class="w-full md:w-56 cursor-pointer hover:text-theme-secondary transition duration-200 border-b-2 border-t-2 md:border-t-0 flex justify-center"
          >
            <a
              @click.prevent="
                isOpen = pakalpojums.id;
                currentIndex = 0;
              "
              href="#"
              :class="isOpen === pakalpojums.id ? ' border-theme-secondary' : ''"
              class="py-5 md:border-b-0 border-b-4"
              >{{ pakalpojums.name }}</a
            >
          </li>
        </ul>
      </div>

      <div class="mt-16">
        <!-- Tab Content -->
        <template v-for="pakalpojums in pakalpojumi" :key="pakalpojums.id">
          <div
            v-show="isOpen === pakalpojums.id"
            class="grid gap-8 lg:gap-16 lg:grid-cols-2 items-center"
          >
            <div class="relative flex flex-col items-center">
              <transition name="fade" mode="out-in">
                <img
                  v-if="isOpen === pakalpojums.id"
                  :key="pakalpojums.details.images[currentIndex]"
                  class="z-10 w-2/5 scale-90 hover:scale-105 transform transition-transform duration-500 ease-in-out cursor-pointer"
                  :src="pakalpojums.details.images[currentIndex]"
                  @click="openModal"
                />
              </transition>
              <div class="flex justify-center items-center space-x-2 mt-5">
                <span v-if="currentIndex > 0" @click="prevDot" class="cursor-pointer">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    class="h-6 w-6 text-[#FA5757] hover:scale-110 duration-100"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M15 19l-7-7 7-7"
                    />
                  </svg>
                </span>
                <span
                  v-for="(dot, index) in visibleDots"
                  :key="index"
                  @click="currentIndex = dot.index"
                  class="cursor-pointer"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    class="h-6 w-6 text-[#FA5757] hover:scale-110 duration-100"
                  >
                    <circle
                      v-if="currentIndex === dot.index"
                      cx="12"
                      cy="12"
                      r="10"
                      stroke="currentColor"
                      stroke-width="2"
                      fill="currentColor"
                    ></circle>
                    <circle
                      v-else
                      cx="12"
                      cy="12"
                      r="10"
                      stroke="currentColor"
                      stroke-width="2"
                      fill="transparent"
                    ></circle>
                  </svg>
                </span>
                <span
                  v-if="currentIndex < pakalpojums.details.images.length - 1"
                  @click="nextDot"
                  class="cursor-pointer"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    class="h-6 w-6 text-[#FA5757] hover:scale-110 duration-100"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M9 5l7 7-7 7"
                    />
                  </svg>
                </span>
              </div>
            </div>
            <div>
              <h3
                class="font-bold text-xl md:text-2xl lg:text-3xl text-center lg:text-left mt-4"
              >
                {{ pakalpojums.details.title }}
              </h3>
              <p class="mt-2 text-gray-700 text-center lg:text-left">
                {{ pakalpojums.details.description }}
              </p>
            </div>
          </div>
        </template>
        <!-- Tab Content -->
      </div>
    </section>
  </div>
  <!-- Pakalpojumi Section End -->

  <ImageModal
    :show="showModal"
    :imageSrc="pakalpojumi[isOpen - 1].details.images[currentIndex]"
    @close="closeModal"
  />
</template>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
