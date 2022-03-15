<template>
  <div class="main">
    <div class="page-title">
      <h2><b>03</b>space launch 101</h2>
    </div>
    <div class="page-content" v-if="technology">
      <div class="item-menu">
        <span :class="index === 0 ? 'selected' : ''" @click="index = 0">1</span>
        <span :class="index === 1 ? 'selected' : ''" @click="index = 1">2</span>
        <span :class="index === 2 ? 'selected' : ''" @click="index = 2">3</span>
      </div>
      <div class="item-content">
        <h2 class="item-common">the terminology...</h2>
        <h1 class="item-name">{{ technology[index].name }}</h1>
        <p class="item-description">{{ technology[index].description }}</p>
      </div>
      <div class="item-img">
        <img
          :src="require(`@/static/${width > 1050 ? technology[index].images.portrait : technology[index].images.landscape}`)"
          style="width: 100%"
        />
      </div>
    </div>
  </div>
</template>
<script>
import data from "../util/data.json";

export default {
  name: "TechnologyPage",
  data() {
    return {
      technology: null,
      index: 0,
      width: null,
    };
  },
  mounted() {
    this.technology = data.technology;
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
    }
  }
};
</script>
<style scoped>
.main {
  display: flex;
  flex-direction: column;
  background-image: url("@/static/technology/background-technology-desktop.jpg");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  min-height: 100vh;
  padding: 12% 0 0 10%;
}

.page-title h2 {
  text-transform: uppercase;
  font-family: "barlow";
  letter-spacing: 4px;
  font-weight: 400;
}

.page-title h2 b {
  margin-right: 1rem;
  color: hsla(0, 0%, 100%, 0.425);
}

.page-content {
  display: grid;
  grid-template-columns: 0.18fr 1.1fr 0.9fr;
  grid-template-areas: "menu content image";
  gap: 5%;
  margin-top: 1rem;
}

.item-img {
  grid-area: image;
}

.item-menu {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  grid-area: menu;
}

.item-menu span {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.7rem;
  font-family: "bellefair";
  border-radius: 50%;
  aspect-ratio: 1;
  border: 1px solid rgba(255, 255, 255, 0.212);
  cursor: pointer;
}

.item-menu span:hover {
  border: 1px solid rgb(255, 255, 255);
}

.selected {
  background-color: var(--white);
  color: var(--dark);
}

.item-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  grid-area: content;
}

.item-common {
  font-family: "barlow";
  font-size: clamp(12px, 2vw, 16px);
  color: var(--light);
  text-transform: uppercase;
  font-weight: 400;
  letter-spacing: 2.35px;
}

.item-name {
  font-size: clamp(28px, 4vw, 56px);
  font-weight: normal;
  font-family: "bellefair";
  text-transform: uppercase;
  letter-spacing: -2px;
}

.item-description {
  text-transform: initial;
  color: var(--light);
  font-size: clamp(0.7rem, 2vw, 1rem);
  font-weight: 400;
  line-height: 180%;
  max-width: 90%;
  margin-top: 1rem;
}

@media (max-width: 1050px) {
  .main {
    padding: max(15%, 100px) 3%;
    justify-content: center;
    background-image: url("@/static/technology/background-technology-tablet.jpg");
  }
  .page-content {
    grid-template-columns: 1fr;
    grid-template-areas:
      "image"
      "menu"
      "content";
    padding: 3rem 0 0;
  }

  .item-menu {
    flex-direction: row;
    justify-content: center;
  }

  .item-menu span {
    font-size: 2rem;
    font-family: "bellefair";
    padding: 2rem;
    border-radius: 50%;
    width: 60px;
    height: 60px;
    margin: 0 1rem;
  }

  .item-content {
    align-items: center;
  }

  .item-description {
    text-align: center;
    width: 80%;
  }
}
@media (max-width: 500px) {
  .main {
    background-image: url("@/static/technology/background-technology-mobile.jpg");
  }
  .page-title {
    font-size: 0.7rem;
    align-self: center;
  }

}
</style>

