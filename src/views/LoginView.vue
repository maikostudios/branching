<script>
import { signInWithEmailAndPassword, auth, signOut, getAuth } from "@/auth";
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async signIn() {
      try {
        const { email, password } = this;
        const { user } = await signInWithEmailAndPassword(
          auth,
          email,
          password
        );
        console.log(user);
      } catch (error) {
        console.log("Error al iniciar sesión:", error.message);
      }
    },
    async logout() {
      const auth = getAuth();
      signOut(auth)
        .then(() => {
          // Sign-out successful.
          alert("Sign-out successful.");
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
    <h2>Iniciar sesión</h2>
    <input v-model="email" type="email" placeholder="Correo electrónico" />
    <input type="password" v-model="password" placeholder="Contraseña" />

    <button @click="signIn">Iniciar Sesión</button>
    <button @click="logout">Cerrar sesión</button>
  </div>
</template>
