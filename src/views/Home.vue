<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <button @click="signout">Logout</button>
  </div>
</template>

<script>
import firebase from "firebase";
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  },
  methods: {
    signout: function() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.replace("login");
        });
    }
  }
};
</script>
