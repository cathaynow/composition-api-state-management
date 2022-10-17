<template>
  <div class="about">
    <h1>Counter works everywhere!:</h1>
    <div :style="{ color: store.state.colorCode }">
      <h2>{{ store.state.counter }}</h2>
    </div>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  setup() {
    const store = inject("store");
    return {
      store,
    };
  },
};
</script>
