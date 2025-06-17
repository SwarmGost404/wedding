<script setup lang="ts">
import { ref, onMounted } from 'vue';
import DMmode from './DMmode.vue';

interface TimeLeft {
  days: number;
  hours: number;
  minutes: number;
  seconds: number;
}

const targetDate = new Date('2025-07-20T12:00:00')

const timeLeft = ref<TimeLeft>({
  days: 0,
  hours: 0,
  minutes: 0,
  seconds: 0,
});

const isActive = () => {
  const interval = setInterval(() => {
    const now = new Date();
    const difference = targetDate.getTime() - now.getTime();
    
    if (difference <= 0) {
      clearInterval(interval);
      timeLeft.value = { days: 0, hours: 0, minutes: 0, seconds: 0 };
      return;
    }

    const days = Math.floor(difference / (1000 * 60 * 60 * 24));
    const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
    const seconds = Math.floor((difference % (1000 * 60)) / 1000);

    timeLeft.value = { days, hours, minutes, seconds };
  }, 1000);
};

onMounted(() => {
  isActive();
});
</script>
<template>
    <div class="flex items-center backdrop-blur-lg fixed sm:relative sm:w-[400px] w-[100%] top-0 border h-[100px] sm:h-[100px] p-6">
      <p class="w-[50%] text-xl">До нашей встречи</p>
      <div class="flex w-[50%]">
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
      <DMmode />
    </div>
</template>
<style>

</style>