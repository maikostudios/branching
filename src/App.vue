<script>
import { RouterLink, RouterView } from "vue-router";

export default {
  name: "App",
  methods: {
    async logout() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          alert("Successfully logged out");
          this.$router.push("/");
        })
        .catch((error) => {
          alert(error.message);
          this.$router.push("/");
        });
    },
  },
};
</script>

<template>
  <div>
    <router-link to="/">Home</router-link> ||
    <router-link to="/registro">Registro</router-link> ||
    <router-link to="/login">Login</router-link>

    <router-view></router-view>
  </div>
</template>

<style scoped></style>
