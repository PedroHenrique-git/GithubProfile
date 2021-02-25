<template>
  <Header msg="Github profile app"/>
  <Index msg="Esta é a index da aplicação"/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Header from './components/Header.vue';
import Index from './components/Index.vue';

export default defineComponent({
  name: 'App',
  components: {
    Header,
    Index,
  },
});
</script>

<style>

  * {
    font-family: 'Roboto', sans-serif;
    margin: 0;
    padding: 0;
  }

  body {
    background: rgb(66, 68, 83);
  }

</style>
