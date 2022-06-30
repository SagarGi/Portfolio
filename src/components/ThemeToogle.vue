<template>
  <ToggleButton
    :color="{
      checked: '#F3F3F3',
      unchecked: '#FF6388',
    }"
    width="90"
    height="47"
    @change="switchTheme"
    v-model="darktheme"
  />
</template>

<script>
import { ToggleButton } from "vue-js-toggle-button";
export default {
  components: {
    ToggleButton,
  },
  data() {
    return {
      darktheme: false,
    };
  },
};
</script>

<style></style>
