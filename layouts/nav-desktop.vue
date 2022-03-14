<template>
  <div>
    <v-app-bar class="navbar" height="80" absolute color="transparent" flat>
      <div class="logo-img">
        <v-img
          :src="require('@/static/shared/logo.svg')"
          max-width="50px"
          aspect-ratio="1"
        />
      </div>
      <v-spacer class="divider"> </v-spacer>
      <div class="menu-items">
        <NuxtLink
          v-for="item in menu"
          :key="item.name"
          :to="item.name"
          class="menu-item"
        >
          <b>{{ item.number }}</b>
          <span>{{ item.name.replace("/", "") }}</span>
          <div v-if="getSelected(item.name)" class="selected"></div>
        </NuxtLink>
      </div>
    </v-app-bar>
  </div>
</template>
<script>
export default {
  name: "NavDesktop",
  props: {
    menu: {
      type: Array,
      default: null,
    },
  },
  methods: {
    getSelected(name) {
      return this.$nuxt.$route.path.includes(name);
    },
  },
};
</script>

<style scoped>
.navbar {
  padding: 1.5rem 0 0 2rem;
}

.logo-img {
  padding: 1rem;
  display: flex;
  align-items: center;
}

.divider {
  margin: 0 -1.5rem 0 3rem;
  border-bottom: 1px solid rgba(187, 185, 185, 0.363);
  z-index: 999999;
}

.menu-items {
  height: 80px;
  width: clamp(600px, 60%, 100%);
  background-color: rgba(255, 255, 255, 0.096);
  backdrop-filter: blur(20px);
  display: flex;
  align-items: center;
  padding: 0 1rem 0 7%;
  font-family: "barlow";
  font-size: 1rem;
  letter-spacing: 2px;
  margin-right: -1rem;
}

.menu-item {
  position: relative;
  margin: 0 1.5rem;
  cursor: pointer;
  height: 100%;
  display: flex;
  align-items: center;
  text-decoration: none;
  color: white;
}

.menu-item:hover::after {
  display: block;
  content: " ";
  position: absolute;
  bottom: 0;
  border-bottom: 2px solid rgba(255, 255, 255, 0.473);
  width: 100%;
  height: 2px;
}

.selected {
  position: absolute;
  bottom: 0;
  border-bottom: 2px solid white;
  width: 100%;
  height: 2px;
}

.menu-item span {
  margin-left: 5px;
  text-transform: uppercase;
}

@media (max-width: 900px) {
  .navbar {
    padding: 0;
  }

  .menu-items {
    padding: 0 1rem;
    background-color: rgba(255, 255, 255, 0.048);
    backdrop-filter: blur(0px);
  }

  .divider {
    border: none;
  }
}
</style>
