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
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed&family=Bellefair&display=swap');

:root {
  --dark: hsl(230, 35%, 7%);
  --light: hsl(231, 77%, 90%);
  --white: hsl(231, 77%, 90%);
}

* {
  font-family: "Bellefair";
  background-color: var(--dark);
  color: var(--white);
}
</style>
