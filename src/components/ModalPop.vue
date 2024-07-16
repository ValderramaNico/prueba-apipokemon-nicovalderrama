<template>
  <div v-show="visible" class="modal-overlay">
    <div class="modal-content">
      <slot></slot>
      <img class="backgroundModal"
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Red_X.svg/240px-Red_X.svg.png"
        alt=""
      />
      <button class="modalButton" @click="closeModal">Cerrar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalPop",
  props: {
    visible: {},
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
  text-align: center;
  padding: 1rem;
  row-gap: 2rem;
  width: 318px;
  height: 450px;
  border-radius: 15px;
  background: #e0e0e0;
  box-shadow: 15px 15px 30px #bebebe, -15px -15px 30px #ffffff;
  background-image: url("https://i.pinimg.com/474x/73/f9/5c/73f95cb31b44736f4ce3adc075d57732.jpg");
  background-size: cover;
  background-repeat: no-repeat;
}

.modal-overlay-hidden {
  display: none;
}

.modalButton {
  margin-top: 45px;
  width: 90px;
  height: 30px;
}

.backgroundModal {
  width: 80px;
  height: 80px;
  margin-bottom: 50px;
}
</style>
