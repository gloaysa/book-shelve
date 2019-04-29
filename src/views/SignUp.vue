<template>
  <div class="sign-up">
    <p class="sign-up-text">Create account</p>
    <div class="sign-up-form">
      <input class="sign-up-form-input" v-model="email" type="text" placeholder="Email"><br>
      <input class="sign-up-form-input" v-model="password" type="password" placeholder="Pass"><br>
      <button class="sign-up-form-button" @click="signUp">Sign Up</button>
      <span class="sign-up-form-go-back">
        go back to <router-link to="/login">login</router-link>
      </span>
    </div>
  </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: 'SignUp',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    signUp() {
      firebase.auth().createUserWithEmailAndPassword(this.email, this.password)
        .then(
          (user) => {
            this.$router.replace('home');
            console.log('account created', user);
          },
          (err) => {
            console.log('error', err.message);
          }
        );
    }
  }
};
</script>

<style scoped lang="scss">
  .sign-up {
    margin-top: 40px;
    &-form {
      &-input {
        margin: 10px 0;
        width: 20%;
        padding: 15px;
      }
      &-button {
        margin-top: 10px;
        width: 10%;
        cursor: pointer;
      }
      &-go-back {
        display: block;
        margin-top: 20px;
        font-size: 11px;
      }
    }
  }
</style>
