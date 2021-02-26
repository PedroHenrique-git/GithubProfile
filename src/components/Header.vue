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
  @import url(../assets/css/header.css);
</style>
