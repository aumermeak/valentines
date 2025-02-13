<template>
  <div class="relative flex items-center justify-center min-h-screen bg-pink-100 overflow-hidden">
    <div class="bg-white shadow-lg rounded-2xl p-6 text-center max-w-sm">
      <div class="relative">
        <img class="heart-shaped w-32 h-32 mx-auto border-4 border-pink-400 shadow-md" src="/kyle.jpg"
          alt="Crush's Profile Picture" />
        <div
          class="absolute -top-2 -right-2 bg-red-500 text-white w-8 h-8 rounded-full flex items-center justify-center text-xl">
          ❤️
        </div>
      </div>

      <h2 class="mt-4 text-2xl font-bold text-gray-800">Kyle Renzine Del Prado</h2>
      <p class="text-pink-500 font-medium">My Valentine 💖</p>

      <p class="mt-4 text-gray-600">
        Every moment with you feels like a dream,
        and I can't help but fall for you every single day.
      </p>
      <p class="mt-4 text-gray-600">yieee <3 </p>

          <div class="mt-6">
            <button @click="acceptLove"
              class="px-4 py-2 bg-pink-500 text-white rounded-lg shadow-md hover:bg-pink-600 transition mr-3">
              Be My Valentine? 💌
            </button>

            <!-- "No :(" Button until clicked 10 times, then replace with "Yes! 💖" -->
            <button v-if="noClicks < 10" @click="rejectLove"
              class="px-4 py-2 bg-pink-500 text-white rounded-lg shadow-md hover:bg-pink-600 transition">
              No :(
            </button>

            <button v-else @click="acceptLove"
              class="px-4 py-2 bg-green-500 text-white rounded-lg shadow-md hover:bg-green-600 transition">
              Yes! 💖
            </button>
          </div>
    </div>

    <!-- Random Yes Buttons -->
    <div v-for="(btn, index) in yesButtons" :key="index" :style="{ top: btn.y + 'px', left: btn.x + 'px' }"
      class="absolute">
      <button class="px-4 py-2 bg-green-500 text-white rounded-lg shadow-md hover:bg-green-600 transition">
        Yes! 💖
      </button>
    </div>

    <!-- Exploding Hearts -->
    <div v-for="(heart, index) in hearts" :key="index"
      :style="{ top: heart.y + 'px', left: heart.x + 'px', opacity: heart.opacity }"
      class="absolute text-red-500 text-3xl animate-heart">
      ❤️
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const yesButtons = ref([]);
const noClicks = ref(0);
const hearts = ref([]);

const rejectLove = () => {
  if (noClicks.value < 9) { // 10th click will replace the "No :("
    const x = Math.random() * window.innerWidth * 0.8;
    const y = Math.random() * window.innerHeight * 0.8;
    yesButtons.value.push({ x, y });
  }
  noClicks.value++;
};

const acceptLove = () => {
  createHearts(); // Trigger the heart explosion
  setTimeout(() => {
    router.push("/yes"); // Redirect after animation
  }, 2000);
};

const createHearts = () => {
  for (let i = 0; i < 30; i++) {
    setTimeout(() => {
      hearts.value.push({
        x: Math.random() * window.innerWidth,
        y: Math.random() * window.innerHeight,
        opacity: 1
      });

      setTimeout(() => {
        hearts.value.shift();
      }, 1500);
    }, i * 50);
  }
};
</script>

<style>
/* ❤️ Heart Animation */
@keyframes heartExplosion {
  0% {
    transform: scale(1) translateY(0);
    opacity: 1;
  }

  100% {
    transform: scale(2) translateY(-100px);
    opacity: 0;
  }
}

.animate-heart {
  animation: heartExplosion 1.5s ease-out forwards;
  position: absolute;
}

/* 💖 Heart-Shaped Image */
.heart-shaped {
  clip-path: polygon(50% 15%, 61% 0, 75% 0, 90% 10%, 100% 25%, 100% 40%,
      95% 55%, 85% 65%, 70% 80%, 50% 95%, 30% 80%, 15% 65%,
      5% 55%, 0 40%, 0 25%, 10% 10%, 25% 0, 39% 0);
}
</style>
