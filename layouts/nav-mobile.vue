<template>
  <div>
    <v-app-bar class="navbar" height="60" absolute color="transparent" flat>
      <v-img
        :src="require('@/static/shared/logo.svg')"
        max-width="40px"
        aspect-ratio="1"
      />
      <v-spacer></v-spacer>
      <v-img
        :src="require('@/static/shared/icon-hamburger.svg')"
        max-width="25px"
        aspect-ratio="1"
        @click.stop="drawer = !drawer"
      />
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" fixed right class="drawer">
      <v-img
        class="icon-close"
        :src="require('@/static/shared/icon-close.svg')"
        max-width="30px"
        aspect-ratio="1"
        @click.stop="drawer = !drawer"
      />
      <div class="menu-items">
        <NuxtLink
          v-for="item in menu"
          :key="item.name"
          :to="item.name"
          class="menu-item"
        >
          <b>{{ item.number }}</b>
          <span>{{ item.name }}</span>
        </NuxtLink>
      </div>
    </v-navigation-drawer>
  </div>
</template>
<script>
export default {
  name: "NavMobile",
  props: {
    menu: {
      type: Array,
      default: null,
    },
  },
  data() {
    return {
      drawer: false,
    };
  },
};
</script>
<style scoped>
.navbar {
  padding: 0.7rem;
}

.drawer {
  display: flex;
  flex-direction: column;
  padding: 2rem 2rem 2rem 3rem;
  z-index: 11;
  background-color: rgba(255, 255, 255, 0.096);
  backdrop-filter: blur(30px);
  width: 425px !important;
}

.icon-close {
  margin-left: auto;
}

.menu-items {
  display: flex;
  flex-direction: column;
  font-family: "barlow";
  font-size: 2rem;
  letter-spacing: 2px;
  margin-top: 4rem;
}

.menu-item {
  margin: 1rem 0;
  text-decoration: none;
  color: white;
}
</style>
