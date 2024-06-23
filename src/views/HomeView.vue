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
          <h5 class="lg:text-xl lg:text-left lg:font-bold lg:text-white">Bellyz G</h5>
          <ul>
            <li class="text-white">
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://www.youtube.com/@BellyzGalliano">Youtube</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://open.spotify.com/artist/3nXYF6cApkYqlgBeK6QMwV?si=vOclef2JQuaTLtWt9v32OA">Spotify</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://music.apple.com/kh/artist/bellyz-g/1623654895">Apple Music</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://x.com/BellyzGalliano?t=jliltRPP_G2ZKqkU6B5_bA&s=35">X</a>
              <a class="p-4 hover:underline decoration-sky-400 underline-offset-4" href="https://www.tiktok.com/@bellyz_g?_t=8nREYoENq7N&_r=1">TikTok</a>
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
            <div class="flex p-4 items-center">
              <img class="w-24" src="/spotify.png" alt="">
              <img class="ml-4 w-24" src="/apple.png" alt="">
              <img class="ml-4 w-32" src="/youtube.png" alt="">
            </div>
            <h1 class="text-6xl font-bold">Bellyz G</h1>
            <p class="font-bold text-lg pt-4">- Introduction</p>
            <p class="text-3xl font-semibold pt-4">Music Artist, Song Writer and<span class="block">Music Producer, based in Cambodia.</span>
            </p>
            <p class="text-md pt-4"><span class="text-4xl font-serif">"</span>Bong Srolanh Oun Neath tae mnek kot<span class="text-4xl font-serif">"</span> </p>
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
        <h5 class="text-7xl font-extrabold"></h5>
      </div>

      <div class="inlineblock pt-8">
        <div class="flex justify-center items-center">
          <img class="w-72 sm:w-80 md:w-96 object-cover bg-transparent" src="/pf1.png">
        </div>
        <h1 class="text-5xl sm:text-4xl md:text-5xl font-bold text-center pt-7">Bellyz G</h1>
        <p class="font-bold text-xl pt-2 text-center">- Introduction</p>
        <p class="text-md sm:text-xl md:text-2xl font-semibold pt-7 text-center">Music Artist, Song Writer and Music Producer,
        </p>
        <p class="text-md sm:text-xl md:text-2xl font-semibold text-center">Based in Cambodia.</p>
        <p class="text-md text-center"><span class="text-4xl font-serif">"</span>Bong Srolanh Oun Neath tae mnek kot<span class="text-4xl font-serif">"</span> </p>
        <div class="flex pt-4 justify-center">
          <a href="#2nd" class="p-3 border border-1 transition duration-100 delay-100 mr-6">Check Out My Music</a>
          <a @click="ModalOpen = true"
            class="cursor-pointer py-3 px-6 border border-1 transition duration-100 delay-100">Follow Me</a>
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

<main  id="2nd" class="container lg:max-w-full lg:min-h-screen xs:w-[500px] xs:h-[200px] bg-black flex justify-center items-center">
<div class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:p-4 p-2">
<div class=" rounded-[30px]">
    <div class="inline-block justify-between items-center">
      <div class="flex justify-center lg:justify-start items-center p-4">
        <img class="w-20" src="/spotify.png" alt="">
      <h5 class="lg:text-7xl text-5xl text-center font-bold pl-4 text-white">Spotify</h5>
    </div>
    <h1 class="lg:text-xl text-sm lg:text-left font-san p-4 text-white justify-center lg:justify-start text-center">Follow my Spotify Channel, Spotify Channel: Bellyz G </h1>
      <iframe class="lg:w-[1470px] lg:h-[600px] rounded-sm lg:rounded-[45px] p-2" src="https://open.spotify.com/embed/artist/3nXYF6cApkYqlgBeK6QMwV?utm_source=generator&theme=0" width="100%" height="352" frameBorder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
    </div>
  </div>
</div>
</main>

<main class="container lg:max-w-full lg:min-h-screen xs:w-[500px] xs:h-[200px] bg-black flex justify-center items-center pb-24">
<div
  class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:p-4">
  <div class=" rounded-[30px}">
    <div class="inline-block justify-between items-center">
      <div class="flex justify-center lg:justify-start items-center p-4">
        <img class="w-20" src="/youtube.png" alt="">
      <h5 class="lg:text-7xl text-5xl text-center font-bold pl-4 text-white">Youtube</h5>
    </div>
      <h1 class="lg:text-xl text-sm lg:text-left font-san p-4 text-white justify-center items-center lg:justify-start text-center">Follow me by Subscribed to my Youtube Channel, Youtube Channel: https://www.youtube.com/@BellyzGalliano </h1>
      <iframe class="lg:w-[1470px] lg:h-[600px] rounded-sm lg:rounded-[45px] lg:p-2 pl-8" src="https://www.youtube.com/embed/mCpIt6ZMxTw" title="Bellyz G - WIFEY (Official Audio)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
  </div>

</div>
</main>

<main class="container max-w-full min-h-screen xs:w-[500px] xs:h-[200px] bg-black flex justify-center items-center">

<div
  class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] p-4 flex justify-center">
  <div class=" rounded-[30px}">
    <div class="inline-block justify-center items-center">
      <div class="flex justify-center items-center p-4">
        <img class="w-20" src="/apple.png" alt="">
      <h5 class="lg:text-7xl text-3xl text-center font-bold pl-4 text-white">Apple Music</h5>
    </div>
      <h1 class="lg:text-xl text-sm lg:text-left font-san p-4 text-white justify-center lg:justify-start text-center">You Can also Follow my Apple Music Channel for the Highest Audio Quality Experiences</h1>
      <iframe allow="autoplay *; encrypted-media *;" frameborder="0" height="580" weight="580" style="width:100%;max-width:1470px;overflow:hidden;background:transparent;" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-storage-access-by-user-activation allow-top-navigation-by-user-activation" src="https://embed.music.apple.com/kh/album/sunset-freestyle-single/1753350363"></iframe>
    </div>
  </div>

</div>
</main>


<!-- SKILLS and PROJECTS SECTION -->

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