<template>
  <button type="button" class="btn" >
        {{ symbols }}
  </button>
</template>

<script>
  export default {
    name: 'SimpleButton',
    props: {
      symbols: String
    }
  }
</script>

<style>
button{
  color: aqua;
}
</style>