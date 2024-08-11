<script setup>
import { ref } from "vue";

let mobileNav = ref(false);

let toggleMobileNav = () => {
  mobileNav.value = !mobileNav.value;
};
</script>

<template>
  <!-- Navbar Start -->
  <div class="container mx-auto px-5">
    <header class="flex justify-between py-12 items-center">
      <div class="flex justify-center items-center">
        <div class="h-24 w-24 md:h-24 md:w-24">
          <img src="images/gkmasterworks-logo.png" />
        </div>
        <h1 href="/" class="ml-2 text-2xl font-bold hidden lg:block">GK&METALS</h1>
      </div>

      <nav class="flex justify-end flex-col md:flex-row">
        <!-- Menu Toggler -->
        <button
          @click="toggleMobileNav()"
          type="button"
          class="flex md:hidden focus:outline-none"
        >
          <svg viewBox="0 0 24 24" class="h-6 w-6 fill-current">
            <path
              fill-rule="evenodd"
              d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
            ></path>
          </svg>
        </button>

        <!-- Desktop Menu -->
        <ul
          class="space-x-10 font-theme-heading font-medium items-center hidden md:flex flex-col space-y-7 md:space-y-0 md:flex-row"
        >
          <li class="uppercase hover:text-theme-secondary transition duration-200">
            <a href="#par" v-smooth-scroll>Par mums</a>
          </li>

          <li class="uppercase hover:text-theme-secondary transition duration-200">
            <a href="#pakalpojumi" v-smooth-scroll>Pakalpojumi</a>
          </li>
          <li class="uppercase hover:text-theme-secondary transition duration-200">
            <a href="#faq" v-smooth-scroll>Jautājumi</a>
          </li>
          <li
            class="uppercase bg-theme-secondary px-6 py-2 text-white rounded shadow-md hover:bg-white border-2 border-transparent hover:border-theme-secondary hover:text-theme-secondary cursor-pointer transition duration-200"
          >
            <a href="#sazinies" v-smooth-scroll>Sazinies</a>
          </li>
        </ul>
      </nav>
    </header>

    <!-- Mobile Menu Start-->
    <div v-show="mobileNav">
      <div
        class="absolute px-5 py-12 block z-30 top-0 left-0 w-full h-full bg-gradient-to-b from-theme-dark-blue via-theme-dark-blue-tp to-theme-dark-blue"
      >
        <div class="flex justify-between items-center">
          <div class="flex items-center">
            <h1 href="/" class="text-2xl font-bold text-white">GK&METALS</h1>
          </div>
          <button @click="toggleMobileNav()" type="button" class="focus:outline-none">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="30"
              height="30"
              fill="currentColor"
              class="bi bi-x text-white"
              viewBox="0 0 16 16"
            >
              <path
                d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"
              />
            </svg>
          </button>
        </div>
        <ul
          class="uppercase text-white text-md tracking-widest items-center flex flex-col mt-14"
        >
          <li
            class="hover:text-theme-secondary transition duration-200 py-4 border-t border-b border-theme-grayish-blue w-full text-center"
          >
            <a @click="toggleMobileNav()" href="#par">Par mums</a>
          </li>
          <li
            class="hover:text-theme-secondary transition duration-200 py-4 border-b border-theme-grayish-blue w-full text-center"
          >
            <a @click="toggleMobileNav()" href="#pakalpojumi">Pakalpojumi</a>
          </li>
          <li
            class="hover:text-theme-secondary transition duration-200 py-4 border-b border-theme-grayish-blue w-full text-center"
          >
            <a @click="toggleMobileNav()" href="#faq">Jautājumi</a>
          </li>
          <li
            class="bg-transparent border-2 rounded px-6 py-2 mt-6 w-full text-center cursor-pointer hover:text-theme-secondary transition duration-200"
          >
            <a @click="toggleMobileNav()" href="#sazinies">Sazinies</a>
          </li>
        </ul>
        <div class="flex justify-center items-end h-52">
          <ul class="flex space-x-8">
            <a href="https://www.instagram.com/gkmetals83/">
              <li>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="26"
                  height="26"
                  fill="currentColor"
                  class="bi bi-instagram text-white hover:text-theme-secondary transition duration-200 cursor-pointer"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.9 3.9 0 0 0-1.417.923A3.9 3.9 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.9 3.9 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.9 3.9 0 0 0-.923-1.417A3.9 3.9 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599s.453.546.598.92c.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.5 2.5 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.5 2.5 0 0 1-.92-.598 2.5 2.5 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233s.008-2.388.046-3.231c.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92s.546-.453.92-.598c.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92m-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217m0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334"
                  />
                </svg>
              </li>
            </a>
            <a href="https://www.facebook.com/people/GK-Met%C4%81ls/61563279011833/">
              <li>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="26"
                  height="26"
                  fill="currentColor"
                  class="bi bi-facebook text-white hover:text-theme-secondary transition duration-200 cursor-pointer"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951"
                  />
                </svg>
              </li>
            </a>
            <a href="https://www.whatsapp.com/">
              <li>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="26"
                  height="26"
                  fill="currentColor"
                  class="bi bi-whatsapp text-white hover:text-theme-secondary transition duration-200 cursor-pointer"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M13.601 2.326A7.85 7.85 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c0 1.399.366 2.76 1.057 3.965L0 16l4.204-1.102a7.9 7.9 0 0 0 3.79.965h.004c4.368 0 7.926-3.558 7.93-7.93A7.9 7.9 0 0 0 13.6 2.326zM7.994 14.521a6.6 6.6 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c0-3.626 2.957-6.584 6.591-6.584a6.56 6.56 0 0 1 4.66 1.931 6.56 6.56 0 0 1 1.928 4.66c-.004 3.639-2.961 6.592-6.592 6.592m3.615-4.934c-.197-.099-1.17-.578-1.353-.646-.182-.065-.315-.099-.445.099-.133.197-.513.646-.627.775-.114.133-.232.148-.43.05-.197-.1-.836-.308-1.592-.985-.59-.525-.985-1.175-1.103-1.372-.114-.198-.011-.304.088-.403.087-.088.197-.232.296-.346.1-.114.133-.198.198-.33.065-.134.034-.248-.015-.347-.05-.099-.445-1.076-.612-1.47-.16-.389-.323-.335-.445-.34-.114-.007-.247-.007-.38-.007a.73.73 0 0 0-.529.247c-.182.198-.691.677-.691 1.654s.71 1.916.81 2.049c.098.133 1.394 2.132 3.383 2.992.47.205.84.326 1.129.418.475.152.904.129 1.246.08.38-.058 1.171-.48 1.338-.943.164-.464.164-.86.114-.943-.049-.084-.182-.133-.38-.232"
                  />
                </svg>
              </li>
            </a>
          </ul>
        </div>
      </div>
    </div>
    <!-- Mobile Menu End-->
  </div>
  <!-- Navbar End -->
</template>
