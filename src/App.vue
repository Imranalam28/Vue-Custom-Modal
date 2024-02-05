<template>
  <div id="app">
    <div>
      <label for="titleInput">Modal Title:</label>
      <input type="text" v-model="modalTitleInput" id="titleInput" />
    </div>
    <div>
      <label for="contentInput">Modal Content:</label>
      <input type="text" v-model="modalContentInput" id="contentInput" />
    </div>
    <button @click="openModal">Open Modal</button>
    <transition name="slide-fade">
      <modal-component v-if="showModal" @close="closeModal" :modal-title="modalTitle" :modal-content="modalContent" />
    </transition>
    <div class="overlay" v-if="showModal"></div>
  </div>
</template>

<script>
import ModalComponent from './components/ModalComponent.vue';

export default {
  components: {
    ModalComponent,
  },
  data() {
    return {
      showModal: false,
      modalTitleInput: '',
      modalContentInput: '',
    };
  },
  methods: {
    openModal() {
      this.modalTitle = this.modalTitleInput || 'Default Title';
      this.modalContent = this.modalContentInput || 'Default Content';
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>

<style>
/* Add this style for the overlay */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5); /* Adjust the transparency as needed */
  z-index: 1; /* Make sure the overlay is above other elements */
  pointer-events: auto; /* Enable pointer events on the overlay */
}

.slide-fade-enter-active {
  transition: all 2s ease-out; /* Adjust the duration as needed */
}

.slide-fade-leave-active {
  transition: all 2s cubic-bezier(1, 0.5, 0.8, 1); /* Adjust the duration and easing function */
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

</style>
