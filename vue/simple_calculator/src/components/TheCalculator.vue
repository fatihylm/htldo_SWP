<template>
  <div class="wrapper">
    <div class="main">
      <h1>Simple Calculator</h1>
      <input v-model="currentValue" />
      <div class="row">
        <simple-button
          class="btn"
          Rechenart="+"
          @calculate="calculate"
        ></simple-button>
        <simple-button
          class="btn"
          Rechenart="-"
          @calculate="calculate"
        ></simple-button>
        <simple-button
          class="btn"
          Rechenart="*"
          @calculate="calculate"
        ></simple-button>
        <simple-button
          class="btn"
          Rechenart="/"
          @calculate="calculate"
        ></simple-button>
      </div>
      <simple-button
        id="large"
        class="btn"
        Rechenart="="
        @calculate="calculate"
      ></simple-button>
    </div>
  </div>
</template>
<script>
import SimpleButton from "./SimpleButton.vue";

export default {
  name: "TheCalculator",
  components: {
    SimpleButton,
  },
  data() {
    return {
      previousValue: 0,
      currentValue: "",
      previousOperator: "",
    };
  },
  methods: {
    //Hier werden die Rechenarten definiert und deren Funktion definiert Blessing hat geholfen
    calculate(Rechenart) {
      if (
        (Rechenart === "+") |
        (Rechenart === "-") |
        (Rechenart === "*") |
        (Rechenart === "/")
      ) {
        this.previousValue = parseInt(this.currentValue);
        this.currentValue = "";
        this.previousOperator = Rechenart;
      } else if (Rechenart === "=") {
        if (this.previousOperator === "+") {
          this.currentValue = this.previousValue + parseInt(this.currentValue);
        } else if (this.previousOperator === "-") {
          this.currentValue = this.previousValue - parseInt(this.currentValue);
        } else if (this.previousOperator === "*") {
          this.currentValue = this.previousValue * parseInt(this.currentValue);
        } else if (this.previousOperator === "/") {
          this.currentValue = this.previousValue / parseInt(this.currentValue);
        }
      }
    },
  },
};
</script>
<style>
.wrapper {
  height: 80vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  text-align: center;
  font-weight: 600;
  font-size: 2rem;
}
input {
  width: 80vw;
  height: 5vh;
  margin-bottom: 20px;
  font-size: 2rem;
}

.btn {
  display: flex;
  width: 40%;
  height: 4rem;
  background-color: rgb(170, 170, 170);
  color: rgb(255, 217, 0);
  font-size: 3.5rem;
  line-height: 4rem;
  transition: all 0.5s;
  justify-content: space-evenly;
  align-content: center;
}
.row {
  display: flex;
  flex-direction: row;
  gap: 15px;
}
.btn:hover {
  background-color: black;
  cursor: pointer;
}
#large {
  margin-top: 20px;
  width: 100%;
  height: 6vh;
  background: rgb(170, 170, 170);;
  text-align: center;
  font-size: 3.5rem;
}

#large:hover {
  background-color: rgb(0, 0, 0);
  cursor: pointer;
}
</style>