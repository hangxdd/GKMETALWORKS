<script setup>
import socials from "../data/socials";
import { ChatBubbleLeftRightIcon } from "@heroicons/vue/24/solid";
</script>

<template>
  <!-- Socials Section Start -->
  <div id="sazinies" class="container mx-auto px-5 md:w-4/5">
    <section class="py-16 pt-18">
      <div class="w-4/5 md:w-3/5 mx-auto">
        <h2 class="text-3xl md:text-4xl font-theme-heading font-medium text-center">
          Sazinies
        </h2>
      </div>
      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8 mt-12">
        <div
          v-for="(social, index) in socials"
          :key="social.id"
          class="shadow-lg rounded-lg"
        >
          <div class="flex justify-center mt-12">
            <img :src="social.icon" alt="Social Logo" class="h-16 w-16" />
          </div>
          <h3 class="text-2xl font-theme-heading font-medium text-center mt-6">
            {{ social.title }}
          </h3>
          <p class="text-md font-theme-content text-theme-grayish-blue text-center mt-3">
            {{ social.subTitle }}
          </p>
          <div class="my-7">
            <img class="w-full" src="/images/bg-dots.svg" alt="Dot Backaground" />
          </div>
          <div class="flex justify-center mb-8">
            <LinkButton
              btn-type="primary"
              :link="social.link"
              class="text-sm bg-none flex items-center justify-center"
            >
              <ChatBubbleLeftRightIcon class="h-5 w-5" />
            </LinkButton>
          </div>
        </div>
      </div>
    </section>
  </div>
  <!-- Socials Section End -->
</template>
