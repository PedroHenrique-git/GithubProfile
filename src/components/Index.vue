<template>
    <section class="container">
        <form v-on:submit.prevent="getData" class="form-box">
            <input type="text" id="profile" autocomplete="off" v-model="user">
            <button class="btn-send">search profile</button>
        </form>
    </section>
    <div v-if="isLoading" class="profile-card">
        <img :src="userData.avatar_url || require('../assets/images/user.png')"
        />
        <div class="user-informations">
            <h3>{{ userData.login ? userData.login : "not found" }}</h3>
            <p>total repositories: {{ userData.public_repos ? userData.public_repos : 0}}</p>
            <p>company: {{ userData.company ? userData.company : "none" }}</p>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Index',
  data() {
    return {
      user: '',
      userData: {},
      isLoading: false,
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
      this.user = '';
      this.isLoading = true;
    },
  },
});
</script>

<style scoped>
    @import url(../assets/css/index.css);
</style>
