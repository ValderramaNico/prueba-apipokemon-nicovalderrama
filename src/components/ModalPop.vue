<template>
  <div v-show="visible" class="modal-overlay">
    <div class="modal-content">
      <slot></slot>
      <img
        class="backgroundModal"
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
  z-index: 1000;
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
  padding-bottom: 9rem;
  width: 318px;
  height: 450px;
  border-radius: 15px;
  background: #e0e0e0;
  box-shadow: 15px 15px 30px #bebebe, -15px -15px 30px #ffffff;
  background-image: url("https://i.pinimg.com/474x/73/f9/5c/73f95cb31b44736f4ce3adc075d57732.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  z-index: 1001;
  position: fixed;
}

.modal-overlay-hidden {
  display: none;
}

.modalButton {
    width: 133px;
  margin-top: 45px;
  border-radius: 190px 0px 190px 0px / 150px 0px 150px 0px;
  border: none;
  color: white;
  background-color: #2b73b9;
  font-size: 17px;
  padding: 0.5em 2em;
  border: transparent;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
  position: absolute;
  left: 154px;
  top: 336px;
}

button:hover {
  background: rgb(2, 0, 36);
  background: linear-gradient(
    90deg,
    rgba(30, 144, 255, 1) 0%,
    rgba(0, 212, 255, 1) 100%
  );
}

button:active {
  transform: translate(0em, 0.2em);
}

.backgroundModal {
  width: 80px;
  height: 80px;
  margin-bottom: 50px;
}
</style>
