<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div :style="{ color: store.state.colorCode }" class="counter">
      {{ store.state.counter }}
    </div>
    <div class="counter-squared">
      {{ store.state.counter }}
      <sup>2</sup> = {{ store.getters.counterSeuarded() }}
    </div>
    <div class="buttons">
      <button @click="store.methods.decreaseCounter">-</button>
      <button @click="store.methods.increaseCounter">+</button>
    </div>
    <div>
      <input v-model="colorCode" type="text" placeholder="Enter color code" />
    </div>
  </div>
</template>

<script>
import { inject, computed } from "vue";
export default {
  name: "Home",
  setup() {
    const store = inject("store");

    const colorCode = computed({
      get() {
        return store.state.colorCode;
      },
      set(val) {
        //console.log("val:", val);
        store.methods.setColorCode(val);
      },
    });

    return {
      store,
      colorCode,
    };
  },
};
</script>

<style scoped>
div {
  margin-bottom: 10px;
}
.counter {
  font-size: 80px;
}
.buttons button {
  font-size: 40px;
  width: 100px;
  margin: 0 10px;
}
</style>
