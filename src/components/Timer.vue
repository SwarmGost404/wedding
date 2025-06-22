<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';

interface TimeLeft {
  days: number;
  hours: number;
  minutes: number;
  seconds: number;
}

export default defineComponent({
  name: 'Timer',
  setup() {
    const isDark = ref(false);
    
    const updateTheme = () => {
      if (isDark.value) {
        document.documentElement.classList.add('dark');
        localStorage.setItem('theme', 'dark');
      } else {
        document.documentElement.classList.remove('dark');
        localStorage.setItem('theme', 'light');
      }
    };

    const toggleTheme = () => {
      isDark.value = !isDark.value;
      updateTheme();
    };

    const targetDate = new Date('2025-07-20T12:00:00');
    const timeLeft = ref<TimeLeft>({
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    });

    const startCountdown = () => {
      const interval = setInterval(() => {
        const now = new Date();
        const difference = targetDate.getTime() - now.getTime();
        
        if (difference <= 0) {
          clearInterval(interval);
          timeLeft.value = { days: 0, hours: 0, minutes: 0, seconds: 0 };
          return;
        }

        timeLeft.value = {
          days: Math.floor(difference / (1000 * 60 * 60 * 24)),
          hours: Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)),
          minutes: Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60)),
          seconds: Math.floor((difference % (1000 * 60)) / 1000)
        };
      }, 1000);
    };

    onMounted(() => {
      const savedTheme = localStorage.getItem('theme');
      const systemPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      isDark.value = savedTheme ? savedTheme === 'dark' : systemPrefersDark;
      updateTheme();
      
      startCountdown();
    });

    return {
      isDark,
      toggleTheme,
      timeLeft
    };
  }
});
</script>
<template>
    <header
    @click="toggleTheme"
    class="z-100000 backdrop-blur-sm bg-white/30 flex fixed sm:relative  w-[100%] top-0 border h-[100px] sm:h-[100px] p-6">
      <p class="w-[50%] text-xl">До нашей встречи</p>
      <div class="flex w-[50%] ">
        <div class="text-center">
        <span class=" text-xl font-bold">{{timeLeft.days + " : "}}</span>

        </div>
        <div class="text-center">
          <span class=" text-xl font-bold">{{timeLeft.hours + " : "}}</span>

        </div>
        <div class="text-center">
          <span class=" text-xl font-bold">{{timeLeft.minutes + " : "}}</span>

        </div>
        <div class="text-center">
          <span class=" text-xl font-bold">{{timeLeft.seconds}}</span>

        </div>
      </div>
      <svg
        v-if="!isDark"
        class=" w-4 h-4"
        fill="currentColor"
        viewBox="0 0 20 20"
      >
        <path d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z"></path>
      </svg>
      <svg
        v-else
        class=" w-5 h-5 "
        fill="currentColor"
        viewBox="0 0 20 20"
      >
        <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path>
      </svg>
    </header>
</template>
<style>
header:hover {
  svg {
    fill: #facc15;
    filter: drop-shadow(0 0 8px #facc15);
  }
}
</style>