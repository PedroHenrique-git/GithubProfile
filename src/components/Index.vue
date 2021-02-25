<template>
    <section class="container">
        <form v-on:submit.prevent="getData" class="form-box">
            <input type="text" id="profile" autocomplete="off" v-model="user">
            <button class="btn-send">search profile</button>
        </form>
    </section>
    <ul>
        <li v-for="value in userData" v-bind:key="value">
            {{ value ? value : 'not exists' }}
        </li>
    </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Index',
  data() {
    return {
      user: '',
      userData: {},
    };
  },
  props: {
    msg: String,
  },
  methods: {
    async getData(): Promise<void> {
      if (this.user === '') return;
      const data = await (await fetch(`https://api.github.com/users/${this.user}`)).json();
      this.userData = data;
    },
  },
});
</script>

<style scoped>
    .container {
        margin: 50px 0;

        display: flex;
        justify-content: center;
    }

    .form-box {
        width: 300px;
        height: auto;

        display: flex;
        flex-direction: column;
    }

    .form-box input {
        background: transparent;
        border: 1px solid white;
        border-radius: 5px;
        margin-bottom: 15px;
        height: 50px;
        outline: none;
        padding: .3em;
        font-size: 18px;
        color: #fff;
    }

    .form-box input:focus {
        background: transparent;
    }

    .form-box button {
        background: rgb(39, 39, 39);
        border: none;
        border-radius: 5px;
        cursor: pointer;
        height: 50px;
        outline: none;
        padding: .3em;
        font-size: 18px;
        color: #fff;
    }

    ul {
        width: 500px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        margin: 20px auto;
    }

    ul li {
        white-space: nowrap;
    }
</style>
