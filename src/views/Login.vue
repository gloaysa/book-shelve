<template>
  <div class="login">
    <h3>Sign In</h3>
    <div class="login-form">
      <input class="login-form-input" v-model="email" type="text" placeholder="Email"><br>
      <input class="login-form-input" v-model="password" type="password" placeholder="Password"><br>
      <button class="login-form-button" @click="login">Log in</button>
    </div>
    <p class="login-text">
      You don't have an account?
      <router-link class="login-text-link" to="/sign-up">create one</router-link>
    </p>
  </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: 'login',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    login() {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
        .then(
          (user) => {
            this.$router.replace('home');
            console.log(user);
          },
          (err) => {
            console.log('error', err.message);
          }
        );
      this.$router.replace('home');
    }
  }
};
</script>

<style scoped lang="scss">
  .login {
    margin-top: 40px;
    &-form {
      &-input {
        margin: 10px 0;
        width: 20%;
        padding: 15px;
      }
      &-button {
        margin-top: 20px;
        width: 10%;
        cursor: pointer;
      }
      &-text {
        margin-top: 40px;
        font-size: 13px;
        &-link {
          text-decoration: underline;
          cursor: pointer;
        }
      }
    }
  }
</style>
