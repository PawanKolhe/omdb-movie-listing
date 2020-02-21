<template>
  <div class="modal-container" v-if="modalVisible">
    <div class="modal">
      <div @click="closeModal" class="modal-close"><span class="iconify" data-icon="fa-solid:times" data-inline="false"></span></div>

      <h2>{{ title }}</h2>
      
    </div>
  </div>
</template>

<script>


export default {
  name: 'Modal',
  props: ['modalVisible', 'movieDetail', 'title', 'poster'],
  methods: {
    closeModal() {
      this.$emit('closeModal', false);
    }
  }
}
</script>

<style scoped>
.modal-container {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
  padding: 5%;
  justify-content: center;
  align-items: center;
  overflow: auto;
  display: flex;
}

.modal {
  background-color: #ffffff;
  border-radius: 10px;
  width: 100%;
  max-width: 800px;
  height: 80%;
  position: relative;
  padding: 30px;
  overflow-y: auto;
  overflow-x: hidden;
  font-family: var(--font-family-2);
  color: #212121;
  z-index: 1100;
}

.modal-close {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  border-radius: 10px;
  position: absolute;
  top: 15px;
  right: 15px;
  color: #ffffff;
  background-color: #F39440;
  box-shadow: 0px 0px 15px #ffae3e;
  overflow: hidden;
  cursor: pointer;
}
</style>