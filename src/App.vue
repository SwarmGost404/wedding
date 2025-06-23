<script setup lang="ts">
import Timer from './components/Timer.vue';
import Galery from './components/Galery.vue';

const goInMap = () => {
  window.location.href = "https://yandex.ru/maps/-/CHWoe84L";
}

const goInTg = () => {
  window.location.href = 'https://t.me/myWebbing_bot'
}

const goPay = () => {
  window.location.href = "https://www.tinkoff.ru/rm/r_BwPbHVzgEU.CVpIUrVoDL/dGea497749"
}


</script>

<template>
  <Timer />

  <main class="w-[80%] mt-10%  ml-[10%] relative top-[155px] sm:top-[55px] ">
      <h1 class=" my-[10%]">
        Виктор 
        <br />
        Злата
      </h1>
      <div class="flex items-center gap-6 relative w-[80%] left-[10%] justify-center p-6 my-[10%]">
        <div class=" text-4xltext-2xl font-serif font-medium border-t  border-b  place-items-center ">
          <p>Среда</p>
        </div>
        
        <div class="flex flex-col items-center border-t  border-b my-[10%]">
          <p class="uppercase tracking-wider">Августа</p>
          <p class="font-bold  leading-none">6</p>
          <p>2025</p>
        </div>
        
        <div class="my-[10%] text-2xl font-serif font-medium border-t  border-b  place-items-center ">
          <p>09:00</p>
        </div>
      </div>
      <div>
        <Galery />
      </div>
      <div class="my-[10%]">
        <button @click="goInTg" class="border p-4 text-4xl rounded-[10px] hover:underline ">
          Если хотите отправить фотографии, или пожелания, заходите сюда
        </button>
      </div>
      <div class="my-[10%]">
        <h2>Адрес венчания</h2>
        <p><strong>Церковь Страстотерпца Царевича Алексия в Знаменке</strong>
          <i>ул. Чайковского, 13Б, Петергоф</i>
        </p>
        <button 
          class="my-[20px] text-4xl border p-4 rounded-[10px] hover:underline "
          @click="goInMap"
        >
          Посмотреть на карте
        </button>
      </div>
      <div class="my-[10%]">
        <h2>
          Дресс-код
        </h2>
        <p>
          Чтобы сохранить стиль и атмосферу мероприятия, мы будем рады, если вы поддержите Русскую традицию, и придёте в народном костюме северной традиции
        </p>
      </div>

      <div class="my-[10%]">
        <h2>
          Что дарить?
        </h2>
        <p>
          В качестве подарка мы будем рады вкладу в бюджет нашей семьи. Он точно поможет воплотить воплотить наши мечты в реальность!
        </p>
        <p>* но, если у вас есть очень хорошая идея что подарить, что действительно пригодится в хозяйстве, и у нас этого точно нет</p>
        <div class="w-full ">
          <button @click="goPay" class="my-[20px] text-4xl border p-4 rounded-[10px] hover:underline" >Если вдруг вам удобнее подарить подарок в виде денег, можно сделать это здесь  </button>
        </div>
      </div>
      <div class="hidden  justify-center w-full sm:grid">
        <img class="p-4 border-black border bg-white" src="/public/qrCodeFin.png" alt="">
      </div>
      <footer class=" w-full my-[100px]">
        <div class="w-full my-[100px]">
          
        </div>
      </footer>
    </main>
</template>

<style scoped>
* {
  font-family: "Caveat", cursive;
}
@media (min-width: 768px) {
  p {
  font-size: 180%;
  }
  h2 {
    font-size: 200%;

  }
  h3 {
    font-size: 220%;
  }
  h1 {
    font-size: 6rem;
  }
}

@media (max-width: 767px) {
  h1 {
    font-size: 200%;
  }
  p,
  h2,
  h3,
  span {
    font-size: 130%;
  }

}



</style>
