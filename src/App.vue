<script setup lang="ts">
import Timer from './components/Timer.vue';
const goInMap = () => {
  window.location.href = "https://yandex.ru/maps/-/CHWoe84L";
}



</script>

<template>
  <main class="w-[80%] mt-10% ml-[10%] relative top-[55px] ">
      <h1
        class="text-8xl my-[10%]"
      >
        Виктор 
        <br />
        &
        <br />
        Злата
      </h1>
      <div class="flex items-center gap-6 relative w-[80%] left-[10%] justify-center p-6 my-[10%]">
        <div class=" text-4xltext-2xl font-serif font-medium border-t border-white border-b  place-items-center ">
          <p>Среда</p>
        </div>
        
        <div class="flex flex-col items-center border-t border-white border-b my-[10%]">
          <p class="uppercase tracking-wider">Августа</p>
          <p class="font-bold  leading-none">6</p>
          <p>2025</p>
        </div>
        
        <div class="my-[10%] text-2xl font-serif font-medium border-t border-white border-b  place-items-center ">
          <p>09:00</p>
        </div>
      </div>
      <div class="my-[10%]">
        <h2>Дорогие гости</h2>
        <p>
          Сердца переполняются радостью, и мы хотим, чтобы вы стали частью нашего особенного дня! Приглашаем вас на нашу свадьбу!
        </p>
      </div>
      <div class="my-[10%]">
        <h2>Адрес венчания</h2>
        <p><strong>Церковь Страстотерпца Царевича Алексия в Знаменке</strong>
          <i>ул. Чайковского, 13Б, Петергоф</i>
        </p>
        <button 
          class="my-[20px] text-4xl border-white  "
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
        <h2>До нашей встречи</h2>
        <Timer />
      </div>
      <div class="my-[10%]">
        <h2>
          Что дарить?
        </h2>
        <p>
          В качестве подарка мы будем рады вкладу в бюджет нашей семьи. Он точно поможет воплотить воплотить наши мечты в реальность!
        </p>
        <p>* но, если у вас есть очень хорошая идея что подарить, что действительно пригодится в хозяйстве, и у нас этого точно нет</p>
      </div>
      <footer class="m-[100px] my-[10%]">
          <a class="hover:underline " href="https://t.me/swarmgost">По всем вопросам обращайтесь сюда</a>
      </footer>
    </main>
</template>

<style scoped>
* {
  font-family: "Caveat", cursive;
}
p {
  font-size: 180%;
}
h2 {
  font-size: 200%;

}
h3 {
  font-size: 220%;
}
button {
  border: #fff 1px solid;
  padding: 20px;
  border-radius: 10px;
  
}
button:hover {
  
  box-shadow: 10px 10px 10px #fff;
}

</style>
