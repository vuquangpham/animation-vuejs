<template>
  <div class="container">
    <transition name="para">
      <p v-if="paraIsVisible">This is only visible</p>
    </transition>
    <button @click="togglePara">Toggle Para</button>

    <div class="block"></div>
    <button>Animate</button>
  </div>

  <BaseModal :open="dialogIsVisible" @close="hideDialog">
    <p>This is a test dialog!</p>
    <button @click="hideDialog">Close it!</button>
  </BaseModal>

  <div class="container">
    <button @click="showDialog">Show Dialog</button>
  </div>
</template>

<script>
import BaseModal from "./components/BaseModal.vue";

export default {
  data() {
    return {
      dialogIsVisible: false,
      paraIsVisible: false,
    };
  },
  methods: {
    showDialog() {
      this.dialogIsVisible = true;
    },
    hideDialog() {
      this.dialogIsVisible = false;
    },
    togglePara() {
      this.paraIsVisible = !this.paraIsVisible;
    },
  },
  components: { BaseModal },
};
</script>

<style>
.para-enter-from {
  /* opacity: 0;
  transform: translateY(-30px); */
}
.para-enter-active {
  /* transition: all 0.3s; */
  animation: test 0.3s ease;
}
.para-enter-to {
  /* opacity: 1;
  transform: translateY(0); */
}

.para-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.para-leave-active {
  transition: all 0.3s;
}
.para-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}

@keyframes test {
  0% {
    transform: translateX(-50px);
  }
  100% {
    transform: translateX(100px);
  }
}

* {
  box-sizing: border-box;
}
html {
  font-family: sans-serif;
}
body {
  margin: 0;
}
button {
  font: inherit;
  padding: 0.5rem 2rem;
  border: 1px solid #810032;
  border-radius: 30px;
  background-color: #810032;
  color: white;
  cursor: pointer;
}
button:hover,
button:active {
  background-color: #a80b48;
  border-color: #a80b48;
}
.block {
  width: 8rem;
  height: 8rem;
  background-color: #290033;
  margin-bottom: 2rem;
}
.container {
  max-width: 40rem;
  margin: 2rem auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 2rem;
  border: 2px solid #ccc;
  border-radius: 12px;
}
</style>
