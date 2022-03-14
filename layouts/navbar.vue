<template>
  <div>
    <NavDesktop v-if="width > 700" :menu="menu" />
    <NavMobile v-if="width <= 700" :menu="menu" />
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
      menu: [
        {
          number: "00",
          to: "/",
          name: "home",
        },
        {
          number: "01",
          to: "/destination",
          name: "destination",
        },
        {
          number: "02",
          to: "/crew",
          name: "crew",
        },
        {
          number: "03",
          to: "/technology",
          name: "technology",
        },
      ],
    };
  },
  mounted() {
    this.width = window.innerWidth;
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.width = window.innerWidth;
    },
  },
};
</script>
<style></style>
