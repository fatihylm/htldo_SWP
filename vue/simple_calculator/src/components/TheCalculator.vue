<template>
  <body>
    <div class="Button">
      <simple-button :Rechenart="'+'"></simple-button>
      <simple-button :Rechenart="'-'"></simple-button>
      <simple-button :Rechenart="'/'"></simple-button>
      <simple-button :Rechenart="'*'"></simple-button>
    </div>
  </body>
</template>

<script>
import SimpleButton from "./SimpleButton.vue";

export default {
  components: {
    SimpleButton,
  },
};
</script>

<style>
.body{
    display: flex;
    justify-content: center;
}

.button{
    flex: 1;
    width: 100%;
    
}
</style>

