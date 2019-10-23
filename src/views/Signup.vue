<template>
  <div id="login">
    <h3>Sign up for new account</h3>
    <input type="text" v-model="email" placeholder="Email" />
    <input type="password" v-model="password" placeholder="Password" />
    <button @click="signup">Sign up</button>
    <p>
      <router-link to="/login">Go back to login</router-link>
    </p>
  </div>
</template>

<script>
import firebase from "firebase";

export default {
  name: "signup",
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    signup: function() {
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            this.$router.replace("login");
          },
          error => {
            alert("Opss.. " + error.message);
          }
        );
    }
  }
};
</script>

<style scoped>
</style>