<template>
  <div>
    <div class="toogle-button">
      <ThemeToogle />
    </div>
    <div class="info-section">
      <InfoSection />
    </div>
    <div class="reachout-section">
      <ReachOut />
    </div>
  </div>
</template>

<script>
import ThemeToogle from "./components/ThemeToogle.vue";
import InfoSection from "./components/InfoSection.vue";
import ReachOut from "./components/ReachOut.vue";
export default {
  components: {
    ThemeToogle,
    InfoSection,
    ReachOut,
  },
};
</script>

<style>
body {
  margin: 0px;
}
.toogle-button {
  background: rgb(255, 255, 255);
  display: flex;
  align-items: center;
  justify-content: right;
  height: 10vh;
  padding-right: 150px;
}

.info-section {
  background: rgb(238, 238, 238);
  display: flex;
  align-items: center;
  justify-content: center;
  height: 75vh;
}
.reachout-section {
  background: rgb(255, 255, 255);
  display: flex;
  align-items: center;
  justify-content: center;
  height: 15vh;
}
</style>
