<template>
  <div id="login">
    <h3>Login</h3>
    <input type="text" v-model="email" placeholder="Email" />
    <input type="password" v-model="password" placeholder="Password" />
    <button @click="login">Login</button>
    <p>
      <router-link to="/signup">Opret konto</router-link>
    </p>
  </div>
</template>

<script>
import firebase from "firebase";

export default {
  name: "login",
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    login: function() {
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            this.$router.replace("home");
          },
          error => {
            console.log("Opps.. " + error.message);
          }
        );
    }
  }
};
</script>

<style scoped>
</style>