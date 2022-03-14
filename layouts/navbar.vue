<template>
  <div>
    <NavDesktop v-if="width > 700" />
    <NavMobile v-if="width <= 700"/>
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
  data() {
    return {
      width: null,
    }
  },
  mounted() {
    this.width = window.innerWidth;
    this.$nextTick(()=>{
      window.addEventListener("resize", this.onResize)
    })
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize)
  },
  methods: {
    onResize() {
      this.width = window.innerWidth;
    },
  },
};
</script>
<style></style>
