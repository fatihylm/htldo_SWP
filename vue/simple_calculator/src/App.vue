<template>
  <div class="calculator">
    <div class="input">
      <h1>Simple calculator</h1>
      <the-calculator></the-calculator>
    </div>
    <div class="buttons">
      <simple-button :Rechenart="'+'"></simple-button>
      <simple-button :Rechenart="'-'"></simple-button>
      <simple-button :Rechenart="'*'"></simple-button>
      <simple-button :Rechenart="'/'"></simple-button>
    </div>
    <div class="equals">
      <simple-button :Rechenart="'='"></simple-button>
    </div>
  </div>
</template>

<script>
import SimpleButton from "./components/SimpleButton.vue";
import TheCalculator from "./components/TheCalculator.vue";

export default {
  name: "App",
  components: {
    SimpleButton,
    TheCalculator,
  },
};
</script>

<style>
#app {
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 98vh;
  overflow: hidden;
}

.input {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: rgb(0, 0, 0);
  font-size: 1.5rem;
}

.buttons {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

.equals {
  display: flex;
  justify-content: center;
  align-items: center;
}

.equals .btn {
  width: 20%;
}

.calculator {
  background-color: rgb(89, 167, 0);
  height: 50%;
  width: 50%;
  display: grid;
}
</style>