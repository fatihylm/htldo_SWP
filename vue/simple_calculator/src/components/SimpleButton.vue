<template>
  <div @click="click()" class="btn">{{ this.Rechenart }}</div>
</template>

<script>
export default {
  emits: ["handleClick"],
  props: {
    Rechenart: {
      type: String,
      required: true,
    },
  },
  methods: {
    click() {
      this.$emit("handleClick", this.Rechenart);
    },
  },
};
</script>
<style>
.btn {
  width: 20%;
  height: 4rem;
  background-color: rgb(0, 0, 0);
  color: rgb(17, 121, 31);
  font-size: 3rem;
  line-height: 4rem;
  transition: all 0.5s;
  text-align: center;
}

.btn:hover {
  background-color: rgb(202, 202, 202);
  cursor: pointer;
}
</style>