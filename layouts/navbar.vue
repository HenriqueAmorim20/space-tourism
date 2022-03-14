<template>
  <div>
    <NavDesktop />
    <NavMobile />
  </div>
</template>
<script>
import NavDesktop from "./nav-desktop.vue";
import NavMobile from "./nav-mobile.vue";
export default {
  name: "NavbarLayout",
  components: {
    NavDesktop,
    NavMobile,
  },
};
</script>
<style></style>
