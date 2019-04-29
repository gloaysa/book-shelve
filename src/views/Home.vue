<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <button class="home-logout" @click="logout">Logout</button>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import * as firebase from 'firebase';

export default {
  name: 'home',
  components: {
    HelloWorld,
  },
  methods: {
    logout() {
      firebase.auth().signOut().then(() => {
        this.$router.replace('login');
      });
    }
  }
};
</script>
