<template>
  <button @click="calculate">
    {{ Rechenart }}
  </button>
</template>

<script>
export default {
  emits: ["calculate"],
  name: "SimpleButton",
  props: {
    Rechenart: String,
  },
  data() {
    return [];
  },
  methods: {
    calculate() {
      this.$emit("calculate", this.Rechenart);
    },
  },
};
</script>