<template>
  <div v-if="!showGallery" class="flex items-center justify-center min-h-screen bg-pink-100">
    <div class="bg-white shadow-lg rounded-2xl p-6 text-center max-w-xl">
      <h1 class="text-3xl font-bold text-gray-800">Yay! 🎉</h1>
      <p class="text-pink-500 font-medium mt-2">Happy Valentines, Kyle Renzine Del Prado 💖</p>
      <p class="mt-4 text-gray-600 bg-pink-100 p-2 rounded">
        I just want to tell you how much I appreciate you. From our LM, TG, to now Messenger na naks! this is my way of
        showing how badly I have fallen for you na. I wanted to surprise you kaya tiniis ko na wag muna sabihin sayo
        tong ginagawa kong smol project pero ayun HAHAHAHA. If you would ask why do I like you I would say I like you
        kase you never even once made me feel like I wasn't interesting saka yung mga usapan natin na minsan nauubos na
        araw araw.
        To be honest di pa rin ako makapaniwala na magugustuhan kita basta biglaan nalang and then ayun na head over
        heels na ako
        di rin ako mapananiwala kung bakit tayo nagtagal magkausap now and ayun thankful naman ako for that lagi akong
        thankful sayo.
        I know what I made here is just a simple appreciation and a simple effort but I poured my heart for this because
        it's all I can do for now.
        Happy Valentines Kyle! (ps wag mo ako ighost! eme) I wish you all the best and Goodluck sa acads, lagi mag
        iingat
        future nurseeee!! 💖💖
      </p>

      <div class="mt-6">
        <button @click="$router.push('/')"
          class="px-4 py-2 bg-pink-500 text-white rounded-lg shadow-md hover:bg-pink-600 transition">
          Back to Home 🏠
        </button>
        <button @click="showGallery = true"
          class="px-4 py-2 ml-5 bg-green-500 text-white rounded-lg shadow-md hover:bg-pink-600 transition">
          Click to see cute pics 💖
        </button>
      </div>
    </div>
  </div>

  <!-- Image Gallery -->
  <div v-else class="min-h-screen bg-black flex flex-wrap justify-center items-center gap-4 p-6 relative">
    <button @click="showGallery = false"
      class="absolute top-5 right-5 px-4 py-2 bg-white text-black font-bold rounded-lg shadow-md hover:bg-gray-200 transition">
      ❌ Close
    </button>

    <!-- Manually added images -->
    <img src="public/mik.jpg" class="w-40 h-40 object-cover rounded-lg shadow-lg transform hover:scale-110 transition"
      alt="Picture ko" />
    <img src="public/mik2.jpg" class="w-40 h-40 object-cover rounded-lg shadow-lg transform hover:scale-110 transition"
      alt="Picture ko" />
    <img src="public/mik3.jpg" class="w-40 h-40 object-cover rounded-lg shadow-lg transform hover:scale-110 transition"
      alt="Picture ko" />
    <img src="public/mik4.jpg" class="w-40 h-40 object-cover rounded-lg shadow-lg transform hover:scale-110 transition"
      alt="Picture ko" />
    <img src="public/mik5.jpg" class="w-40 h-40 object-cover rounded-lg shadow-lg transform hover:scale-110 transition"
      alt="Picture ko" />

    <p class="bg-white rounded p-2 text-black">HAHAHAHA PAGBIGYAN MO NA</p>
  </div>

  <!-- Background Music -->
  <audio ref="bgMusic" autoplay loop>
    <source src="/Elliot James Reay - I Think They Call This Love (Lyrics).mp3" type="audio/mpeg">
    Your browser does not support the audio tag.
  </audio>
</template>

<script setup>
import { ref, onMounted } from "vue";

const bgMusic = ref(null);
const showGallery = ref(false);

onMounted(() => {
  if (bgMusic.value) {
    bgMusic.value.play().catch(() => {
      console.log("User interaction needed to play audio.");
    });
  }
});
</script>
