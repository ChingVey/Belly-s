<script setup lang="ts">
import { useDark, useToggle } from '@vueuse/core'
import { Ref, ref } from 'vue';
import { onClickOutside } from '@vueuse/core'

const isDark = useDark()
const toggleDark = useToggle(isDark)

const ModalOpen1 = ref(false)
const ModalOpen = ref(false)
const isModalOpen = ref(false)

const modal = ref(null)
onClickOutside(modal, () => (isModalOpen.value = false))
onClickOutside(modal, () => (ModalOpen.value = false))
onClickOutside(modal, () => (ModalOpen1.value = false))

</script>

<template>
  <main class="container max-w-full min-h-screen bg-black flex justify-center items-center">
    <div class="lg:w-[1500px] lg:h-[800px]">
      <div class="lg:block hidden bg-neutral-900 rounded-[45px] mb-6">
        <div class="flex justify-between items-center p-6">
          <h5 class="lg:text-xl lg:text-left lg:font-bold lg:text-white">Personal Portfolio</h5>
          <ul>
            <li class="text-white">
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://www.youtube.com/@BellyzGalliano">Youtube</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://open.spotify.com/artist/3nXYF6cApkYqlgBeK6QMwV?si=vOclef2JQuaTLtWt9v32OA">Spotify</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://music.apple.com/kh/artist/bellyz-g/1623654895">Apple Music</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://x.com/BellyzGalliano?t=jliltRPP_G2ZKqkU6B5_bA&s=35">X</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://www.tiktok.com/@hellboy_bellyzg?_t=8k4gSsauFjV&_r=1">TikTok</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://www.facebook.com/profile.php?id=100078748996665">Facebok</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://www.instagram.com/xgbelyz?igsh=anN2OWV4bjFja2g=">Instagram</a>
            </li>
          </ul>
        </div>
      </div>

      <div
        class=" lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid-row-3 lg:grid lg:gap-2 lg:p-4 lg:pt-12 hidden">
        <div class="col-span-4 flex justify-around items-center">
          <div class="inlineblock">
            <h1 class="text-6xl font-bold">Anh Ah Ra</h1>
            <p class="font-bold text-lg pt-4">- Introduction</p>
            <p class="text-3xl font-semibold pt-4">Rapper, Song Writter and<span class="block">Music Producer, based in Phnom Penh.</span>
            </p>
            <p class="text-md pt-4"><span class="text-4xl font-serif">"</span> For me willing to learn is a key to be mature <span class="text-4xl font-serif">"</span> </p>
            <div class="flex pt-4">
              <a href="#2nd"
                class="p-4 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100 mr-3">Check Out My Music</a>
              <a @click="ModalOpen1 = true"
                class="cursor-pointer p-4 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100 mr-3">Follow Me</a>
            </div>
          </div>
          <img class="w-[500px] object-cover bg-transparent" src="/pf1.png">
        </div>
      </div>
    </div>

    <teleport to="#modal">
      <transition name="modal">
        <div v-if="ModalOpen1" class="fixed left-0 top-0 w-[100vw] h-[100vh] object-cover flex bg-black/50 justify-center items-center">
          <div class="relative p-12 rounded-2xl" ref="modal">
            <img class="w-full h-screen cursor-pointer" src="/preview.png">
          </div>
        </div>
      </transition>
    </teleport>

    <div class=" w-[1000px] h-[1000px] bg-neutral-900 text-white inlineblock lg:hidden">
      <div class="flex items-center justify-center text-center py-8">
        <h5 class="text-7xl font-extrabold">Product Owner</h5>
      </div>

      <div class="inlineblock pt-8">
        <div class="flex justify-center items-center">
          <img class="w-72 sm:w-80 md:w-96 object-cover bg-transparent" src="/pf1.png">
        </div>
        <h1 class="text-5xl sm:text-4xl md:text-5xl font-bold text-center pt-7">Lor ChingVey</h1>
        <p class="font-bold text-xl pt-2 text-center">- Introduction</p>
        <p class="text-md sm:text-xl md:text-2xl font-semibold pt-7 text-center">Product owner, Frontend Developer and Designer,
        </p>
        <p class="text-md sm:text-xl md:text-2xl font-semibold text-center">Based in Cambodia.</p>
        <p class="text-md text-center"><span class="text-4xl font-serif">"</span>For me willing to learn is a key to be mature <span class="text-4xl font-serif">"</span> </p>
        <div class="flex pt-4 justify-center">
          <a href="#2nd" class="p-3 border border-1 transition duration-100 delay-100 mr-6">Get to Know me</a>
          <a @click="ModalOpen = true"
            class="cursor-pointer py-3 px-6 border border-1 transition duration-100 delay-100">Preview CV</a>
        </div>
      </div>
    </div>
  </main>

  <teleport to="#modal">
    <transition name="modal">
      <div v-if="ModalOpen" class="fixed left-0 top-0 w-[100vw] h-[100vh] flex bg-black/50 justify-center items-center">
        <div class="relative p-12 rounded-2xl shadow-black/100" ref="modal">
          <img class="w-96" src="/preview.png">
        </div>
      </div>
    </transition>
  </teleport>

<!-- SKILLS and PROJECTS SECTION -->

<main id="3rd" class="container max-w-full min-h-screen bg-black flex justify-center items-center">

<div
  class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:p-4">
  <div class=" rounded-[30px}">
    <div class="inline-block justify-between items-center">
      <h5 class="text-7xl text-left font-bold p-2">Mind Map</h5>
      <h1 class="text-xl text-left font-san p-2">I make mind map for the first step of brain storming the project for stakeholder.</h1>
    <h1 class="text-4xl text-left font-sam p-2 "></h1>
    <img class="rounded-[30px] w-[1500px] h-[600px] p-2 items-center" src="" alt="">
    </div>
  </div>

</div>
</main>

<main class="container max-w-full min-h-screen bg-black flex justify-center items-center">

<div
  class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:p-4">
  <div class=" rounded-[30px}">
    <div class="inline-block justify-between items-center">
      <h5 class="text-7xl text-left font-bold p-2">User Story</h5>
      <h1 class="text-xl text-left font-san p-2">I make mind map for the first step of brain storming the project for stakeholder.</h1>
    <h1 class="text-4xl text-left font-sam p-2 "></h1>
    <img class="rounded-[30px] w-[1500px] h-[600px] p-2 items-center" src="" alt="">
    </div>
  </div>

</div>
</main>

<main class="container max-w-full min-h-screen bg-black flex justify-center items-center">

<div
  class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:p-4">
  <div class=" rounded-[30px}">
    <div class="inline-block justify-between items-center">
      <h5 class="text-7xl text-left font-bold p-2">Business Flow</h5>
      <h1 class="text-xl text-left font-san p-2">I make mind map for the first step of brain storming the project for stakeholder.</h1>
    <h1 class="text-4xl text-left font-sam p-2 "></h1>
    <img class="rounded-[30px] w-[1500px] h-[600px] p-2 items-center" src="" alt="">
    </div>
  </div>

</div>
</main>

<!-- SKILLS and PROJECTS SECTION -->

  <main id="4rd" class="container max-w-full min-h-screen bg-black flex justify-center items-center">

    <div
      class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid lg:grid-rows-3 lg:gap-4 lg:p-4 hidden">
      <div class=" rounded-[30px] col-span-2">
        <div class="flex justify-between items-center">
          <h5 class="text-7xl text-left font-bold p-2">Contact</h5>
        </div>
        <h1 class="text-4xl text-left font-san pl-2 "></h1>
        <h1 class="text-4xl text-left font-sam pl-2 "></h1>
      </div>

      <div class=" bg-white rounded-[30px] col-span-2 p-4 flex justify-between">
        <h1 class="text-black font-bold text-7xl">Projects</h1>
      </div>

      <a href="https://github.com/ChingVey"
        class=" bg-violet-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/LorChingVeylogo.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Github</li>
      </a>

      <a href="tel:066849166"
        class=" bg-green-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/IncomingCallIcon.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Phone</li>
      </a>

      <div class=" bg-white rounded-[30px] text-center col-span-2 row-span-2">
      </div>

      <a href="https://www.linkedin.com/in/lor-chingvey-126letsdoit29/"
        class=" bg-sky-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/LinkedInlogo.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Linkedin</li>
      </a>

      <a href="https://t.me/Lor_JingVey"
        class=" bg-rose-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/telegram-svgrepo-com.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Telegram</li>
      </a>

    </div>


    <div class=" w-[1000px] h-[1000px] bg-neutral-900 text-white grid grid-cols-2 gap-4 p-4 lg:hidden">
      <div class=" rounded-[15px] col-span-2">
        <div class="flex justify-center items-center">
          <h5
            class="text-7xl text-white font-bold mt-8">
            Contact</h5>
        </div>

        <h1 class="text-4xl text-left font-san pl-2"></h1>
        <h1 class="text-4xl text-left font-sam pl-2"></h1>
      </div>

      <a href="https://github.com/ChingVey"
        class="bg-violet-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-center p-3">
          <div class="flex items-center">
          <img class="w-12" src="/LorChingVeylogo.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Github</li>
        </div>
        <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
      </a>

      <a href="tel:0889998500"
        class="bg-green-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-center p-3">
          <div class="flex items-center">
          <img class="w-12" src="/IncomingCallIcon.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Phone</li>
        </div>
        <img class="w-12 animate-pulse" src="/Arrow.svg">
      </div>
      </a>

      <a href="https://www.linkedin.com/in/lor-chingvey-126letsdoit29/"
        class="bg-sky-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-cente p-2">
          <div class="flex items-center">
            <img class="w-12" src="/LinkedInlogo.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Linkedin</li>
          </div>
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
      </a>

      <a href="https://t.me/Lor_JingVey"
        class="bg-rose-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-center p-3">
          <div class="flex items-center">
          <img class="w-12" src="/telegram-svgrepo-com.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Telegram</li>
        </div>
        <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
      </a>
    </div>

  </main>
</template>

<style>
.modal-enter-active,
.modal-leave-active {
  transition: all 0.25s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(1.1);
}</style>