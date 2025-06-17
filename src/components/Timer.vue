<script setup lang="ts">
import { ref, onMounted } from 'vue';


interface TimeLeft {
  days: number;
  hours: number;
  minutes: number;
  seconds: number;
}

const targetDate = new Date('2025-07-20T12:00:00'); // Нужно создать Date объект

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
    <div class="flex items-center justify-center gap-4 p-6 ">
      <div class="text-center">
        <span class="text-4xl font-bold ">{{timeLeft.days + " : "}}</span>
        <br />
        дней
      </div>
      <div class="text-center">
        <span class="text-4xl font-bold ">{{timeLeft.hours + " : "}}</span>
        <br />
        часов
      </div>
      <div class="text-center">
        <span class="text-4xl font-bold ">{{timeLeft.minutes + " : "}}</span>
        <br />
        минут
      </div>
      <div class="text-center">
        <span class="text-4xl font-bold ">{{timeLeft.seconds}}</span>
        <br />
        секунд
      </div>
    </div>
</template>
<style>

</style>