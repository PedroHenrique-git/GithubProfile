<template>
  <header class="component_header">
    <h1>{{ msg }}</h1>
  </header>
</template>

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Header',
  props: {
    msg: String,
  },
});

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .component_header {
    height: 80px;

    display: flex;
    justify-content: center;
    align-items: center;
  }
  .component_header h1 {
    border-bottom: 2px solid #fff;
    font-size: 1.3em;
    color: #fff;
    text-transform: uppercase;
    letter-spacing: 2.5px;
    padding-bottom: 10px;
  }
</style>
