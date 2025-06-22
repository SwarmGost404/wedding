<template>
  <div>
    <div
      class="relative w-64 h-80 bg-white p-4 shadow-lg rotate-[-2deg] hover:rotate-0 transition-transform duration-300 cursor-pointer"
      @click="openModal"
      v-if="imageUrl!==null"
    >
      <div class="w-full h-48 bg-gray-200 mb-3 overflow-hidden">
        <img 
          :src="imageUrl" 
          alt="Polaroid Photo" 
          class="w-full h-full object-cover"
        />
      </div>
      
      <div class="text-center py-2 border-t border-gray-200">
        <p class="font-handwritten text-gray-800">{{ caption }}</p>
        <p class="text-xs text-gray-500 mt-1">{{ date }}</p>
      </div>

      <div class="absolute top-2 right-2 w-6 h-6 bg-white opacity-50 rotate-45"></div>
    </div>

    <Teleport to="body">
      <Transition name="modal">
        <div 
          v-if="isOpen"
          class="fixed inset-0 bg-black bg-opacity-50 z-50 flex justify-center items-center p-4"
          @click.self="closeModal"
        >
          <div class="relative w-80 h-105 bg-white p-6 shadow-lg rotate-[-1deg]">
            <!-- Угловой элемент как у поляроида -->
            <div class="absolute top-3 right-3 w-8 h-8 bg-white opacity-50 rotate-45"></div>
            
            <div class="mb-4 w-full h-64 bg-gray-100 overflow-hidden">
              <img 
                v-if="imageUrl!==null"
                :src="imageUrl"
                alt="Enlarged Polaroid Photo" 
                class="w-full h-full object-cover"
              />
            </div>
            
            <div class="text-center py-2 border-t border-gray-200">
              <p class="font-handwritten text-2xl text-gray-800">{{ caption }}</p>
              <p class="text-sm text-gray-500 mt-2">{{ date }}</p>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PolaroidCard',
  props: {
    imageUrl: {
      type: String,
      required: true
    },
    caption: {
      type: String,
      default: 'Мое фото'
    },
    date: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      isOpen: false
    }
  },
  computed: {
    formattedDate(): string {
      if (this.date) return this.date;
      return new Date().toLocaleDateString('ru-RU', { 
        month: 'long', 
        year: 'numeric' 
      });
    }
  },
  methods: {
    openModal(): void {
      this.isOpen = true;
      document.body.classList.add('overflow-hidden');
    },
    closeModal(): void {
      this.isOpen = false;
      document.body.classList.remove('overflow-hidden');
    }
  }
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Caveat&display=swap');
.font-handwritten {
  font-family: 'Caveat', cursive;
}

.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-active .modal-content,
.modal-leave-active .modal-content {
  transition: all 0.3s ease;
}

.modal-enter-from .modal-content,
.modal-leave-to .modal-content {
  transform: scale(0.95) rotate(-5deg);
  opacity: 0;
}
</style>