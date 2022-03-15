<template>
  <div class="main">
    <div class="page-title">
      <h2><b>02</b>meet your crew</h2>
    </div>
    <div class="page-content" v-if="crew">
      <div class="item-content">
        <h2 class="item-role">{{ crew[index].role }}</h2>
        <h1 class="item-name">{{ crew[index].name }}</h1>
        <p class="item-bio">{{ crew[index].bio }}</p>
        <div class="item-menu">
          <span
            :class="index === 0 ? 'selected' : ''"
            @click="index = 0"
          ></span>
          <span
            :class="index === 1 ? 'selected' : ''"
            @click="index = 1"
          ></span>
          <span
            :class="index === 2 ? 'selected' : ''"
            @click="index = 2"
          ></span>
          <span
            :class="index === 3 ? 'selected' : ''"
            @click="index = 3"
          ></span>
        </div>
      </div>
      <div class="item-img">
        <v-img
          :src="require(`@/static/${crew[index].images.png}`)"
          width="100%"
          max-width="550px"
          aspect-ratio="1"
          contain
        />
      </div>
    </div>
  </div>
</template>
<script>
import data from "../util/data.json";

export default {
  name: "CrewPage",
  data() {
    return {
      crew: null,
      index: 0,
    };
  },
  mounted() {
    this.crew = data.crew;
  },
};
</script>
<style scoped>
.main {
  display: flex;
  flex-direction: column;
  background-image: url("@/static/crew/background-crew-desktop.jpg");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  min-height: 100vh;
  padding: 12% 3% 0 10%;
}

.page-title h2 {
  text-transform: uppercase;
  font-family: "barlow";
  font-weight: 400;
  letter-spacing: 4px;
}

.page-title h2 b {
  margin-right: 1rem;
  color: hsla(0, 0%, 100%, 0.425);
}

.page-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-top: 3rem;
}

.item-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.item-name {
  font-size: clamp(28px, 7vw, 56px);
  font-weight: normal;
  font-family: "bellefair";
  text-transform: uppercase;
  letter-spacing: -2px;
}

.item-role {
  font-size: clamp(1rem, 3vw, 1.7rem);
  color: gray;
  font-weight: normal;
  font-family: "bellefair";
  text-transform: uppercase;
}

.item-bio {
  text-transform: initial;
  color: var(--light);
  font-size: clamp(0.7rem, 3vw, 1rem);
  font-weight: 400;
  line-height: 180%;
  max-width: 80%;
}

.item-menu {
  display: flex;
  margin-top: 5rem;
}

.item-menu span {
  position: relative;
  width: 13px;
  aspect-ratio: 1;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.205);
  margin: 0 0.7rem;
  cursor: pointer;
}

.selected {
  background-color: rgb(255, 255, 255) !important;
}

.item-menu span:hover {
  background-color: rgba(255, 255, 255, 0.445);
}

@media (max-width: 1000px) {
  .main {
    padding: max(15%, 100px) 3% 0;
    justify-content: center;
    background-image: url("@/static/crew/background-crew-tablet.jpg");
  }
  .page-content {
    grid-template-columns: 1fr;
    padding-top: 3rem;
  }

  .page-menu span {
    margin: 0 1rem;
  }

  .item-bio,
  .item-name {
    text-align: center;
  }

  .item-content {
    padding: 0 10%;
    align-items: center;
  }

  .item-img {
    display: flex;
    justify-content: center;
    margin-top: 4rem;
  }
}

@media (max-width: 500px) {
  .main {
    background-image: url("@/static/crew/background-crew-mobile.jpg");
  }
  .page-title {
    font-size: 0.7rem;
    align-self: center;
  }

  .item-img {
    width: 100%;
    margin-top: 4rem;
  }

  .item-content {
    padding: 0 0%;
    align-items: center;
  }

  .item-info {
    flex-direction: column;
    align-items: center;
  }
  .item-distance {
    margin: 0 0 2rem 0;
  }

  .item-distance,
  .item-travel {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
