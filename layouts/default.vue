<template>
  <v-app>
    <Navbar />
    <v-main>
      <Nuxt />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Navbar from "./navbar.vue";
import Footer from "./footer.vue";

export default {
  name: "DefaultLayout",
  components: {
    Navbar,
    Footer,
  },
};
</script>

<style>
@font-face {
  font-family: "bellefair";
  src: url("~/assets/Bellefair-Regular.ttf") format("truetype");
}

@font-face {
  font-family: "barlow";
  src: url("~/assets/BarlowCondensed-Regular.ttf") format("truetype");
}

:root {
  --dark: hsl(230, 35%, 7%);
  --light: hsl(231, 77%, 90%);
  --white: hsl(0, 0%, 100%);
}
</style>
