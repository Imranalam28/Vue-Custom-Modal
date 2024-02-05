<template>
  <div class="modal">
    <div class="modal-content">
      <h2>{{ formattedTitle }}</h2>
      <p>{{ formattedContent }}</p>
      <button @click="closeModal">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['modalTitle', 'modalContent'],
  computed: {
    formattedTitle() {
      return `Title: ${this.modalTitle}`;
    },
    formattedContent() {
      return `Content: ${this.modalContent}`;
    },
  },
  methods: {
    closeModal() {
      this.$emit('close');
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 20px;
  background-color: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  width: 400px;
  max-width: 80%;
  border-radius: 8px;
  box-sizing: border-box;
  text-align: center;
  z-index: 2;
}

.modal-content {
  font-family: 'Arial', sans-serif;
  color: #333;
  margin-top: 10px;
}

</style>
