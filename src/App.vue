<template>
  <v-app dark>
    <v-system-bar height="30" app dark v-if="systembar && !isHome">
      Por limitaciones de instagram el conteo de seguidores/seguidos puede no
      ser exacto.
      <v-spacer></v-spacer>
      <v-btn icon @click="systembar = false">
        <v-icon> mdi-close </v-icon>
      </v-btn>
    </v-system-bar>
    <div class="background-svg" v-if="isHome">
      <v-img src="./assets/fondo.svg" height="100%" width="100%"></v-img>
    </div>
    <v-main class="pt-12">
      <router-view />
    </v-main>
    <v-footer
      app
      class="transparent d-flex justify-center align-center flex-xl-column"
    >
      <div v-if="!isHome">
        <Logo x-small />
      </div>
      <div class="mx-4 align-center">for</div>
      <div>
        <v-img
          width="103"
          height="29"
          contain
          src="https://www.instagram.com/static/images/web/mobile_nav_type_logo.png/735145cfe0a4.png"
        >
        </v-img>
      </div>
    </v-footer>
  </v-app>
</template>

<script>
import Logo from "./components/Logo.vue";
export default {
  data() {
    return {
      systembar: true,
    };
  },
  components: {
    Logo,
  },
  computed: {
    isHome() {
      return this.$route.name === "Home";
    },
  },
  name: "App",
  mounted() {
    document.querySelector("html").style.overflow = "hidden";
  },
};
</script>
<style lang="scss">
#app {
  background: #e0e0e0;
}
.background-svg {
  position: fixed;
  height: 100vh;
  width: 100%;
  left: 0%;
  top: 0;
}
.relative {
  position: relative;
}
</style>
