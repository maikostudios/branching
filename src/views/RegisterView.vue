<script>
import { RouterLink, RouterView } from "vue-router";
import { createUserWithEmailAndPassword, auth } from "@/auth";

export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async register() {
      try {
        const userCredential = await createUserWithEmailAndPassword(
          auth,
          this.email,
          this.password
        );
        const user = userCredential.user;
        console.log("Usuario registrado: ", user);
      } catch (error) {
        console.log("Error al registrar:", error.message);
      }
    },
  },
};
</script>

<template>
  <div>
    <h2>Registro</h2>
    <input v-model="email" type="email" placeholder="Correo electrónico" />
    <input type="password" v-model="password" placeholder="Contraseña" />

    <button @click="register">Registrarse</button>
  </div>
</template>

<style scoped></style>
