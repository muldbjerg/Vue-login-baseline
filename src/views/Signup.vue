<template>
  <div id="login">
    <h3>Opret en en ny bruger</h3>
    <input type="text" v-model="email" placeholder="Email" />
    <input type="password" v-model="password" placeholder="Password" />
    <button @click="signup">Opret brugeren</button>
    <p>
      <router-link to="/login">Gå tilbage til login</router-link>
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
            console.log("Din nye konto er oprettet");
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