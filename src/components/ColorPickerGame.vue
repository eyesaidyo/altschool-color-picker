<template>
  <h1>Color Picker Game</h1>

  <div>{{ ans }}</div>

  <button v-for="color in colors" :key="color" @click="matchColor(color)">
    {{ color }}
  </button>
</template>

<script>
import { useMatchColor } from "../composables/useColorMatch";
import { ref } from "vue";
export default {
  setup() {
    const colors = ["green", "red", "blue", "purple"];
    let ans = ref("Pick a color...");
    const matchColor = (color) => {
      let { message } = useMatchColor(color, colors);
      ans.value = message;
    };

    return { ans, matchColor, colors };
  },
};
</script>

<style></style>
