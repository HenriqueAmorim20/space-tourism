<template>
  <div class="main">
    <div class="page-title">
      <h2><b>01</b>pick your destination</h2>
    </div>
    <div class="page-content" v-if="destinations">
      <section class="item-img">
        <v-img
          :src="require(`@/static/${destinations[index].images.png}`)"
          width="90%"
          max-width="400px"
          aspect-ratio="1"
          contain
        />
      </section>
      <aside class="item-content">
        <div class="page-menu">
          <span :class="index === 0 ? 'selected' : ''" @click="index = 0">moon</span>
          <span :class="index === 1 ? 'selected' : ''" @click="index = 1">mars</span>
          <span :class="index === 2 ? 'selected' : ''" @click="index = 2">europa</span>
          <span :class="index === 3 ? 'selected' : ''" @click="index = 3">titan</span>
        </div>
        <h1 class="item-name">{{ destinations[index].name }}</h1>
        <p class="item-description">{{ destinations[index].description }}</p>
        <div class="item-info">
          <div class="item-distance">
            <h4>avg. distance</h4>
            <span>{{ destinations[index].distance }}</span>
          </div>
          <div class="item-travel">
            <h4>est. travel time</h4>
            <span>{{ destinations[index].travel }}</span>
          </div>
        </div>
      </aside>
    </div>
  </div>
</template>
<script>
import data from "../util/data.json";

export default {
  name: "DestinationPage",
  data() {
    return {
      destinations: null,
      index: 0,
    };
  },
  mounted() {
    this.destinations = data.destinations;
  },
};
</script>
<style scoped>
.main {
  display: flex;
  flex-direction: column;
  background-image: url("@/static/destination/background-destination-desktop.jpg");
  background-size: cover;
  background-position: center;
  min-height: 100vh;
  padding: 12% 10% 0;
}

.page-title h2 {
  text-transform: uppercase;
  font-family: "barlow";
  letter-spacing: 4px;
}

.page-title h2 b {
  margin-right: 1rem;
  color: hsla(0, 0%, 100%, 0.425);
}

.page-content {
  display: grid;
  /* justify-content: space-between; */
  grid-template-columns: 1fr 1fr;
  gap: 10%;
  padding: 2rem 0;
}

.page-menu {
  display: flex;
  align-items: center;
  margin-bottom: 1.5rem;
}

.page-menu span {
  margin: 0 2rem 0 0;
  padding: 0 0 0.8rem 0;
  cursor: pointer;
  position: relative;
  font-family: "barlow";
  color: var(--light);
  text-transform: uppercase;
  font-weight: 400;
  letter-spacing: 2.35px;
}

.page-menu span:hover::after {
  display: block;
  content: " ";
  position: absolute;
  width: 100%;
  bottom: 0;
  border-bottom: 2px solid rgba(255, 255, 255, 0.473);
}

.page-menu .selected {
  color: white;
}

.page-menu .selected::after {
  display: block;
  content: " ";
  position: absolute;
  width: 100%;
  bottom: 0;
  border-bottom: 2px solid rgb(255, 255, 255);
}

.item-img {
  display: flex;
  align-items: flex-end;
}

.item-content {
  display: flex;
  flex-direction: column;
}

.item-name {
  font-size: clamp(50px, 10vw, 100px);
  text-transform: uppercase;
  font-family: "bellefair";
  font-weight: 400;
}

.item-description {
  text-transform: initial;
  color: var(--light);
  font-size: clamp(0.7rem, 3vw, 1rem);
  font-weight: 400;
  line-height: 180%;
}

.item-info {
  display: flex;
  justify-content: flex-start;
  margin-top: 3rem;
  padding-top: 1.5rem;
  border-top: 1px solid hsla(231, 76%, 90%, 0.253);
}

.item-distance {
  margin-right: 5rem;
}

.item-info h4 {
  font-family: "barlow";
  font-size: 14px;
  color: var(--light);
  text-transform: uppercase;
  font-weight: 400;
  letter-spacing: 2.35px;
}

.item-info span {
  font-family: "bellefair";
  font-size: 28px;
  text-transform: uppercase;
}

@media (max-width: 900px) {
  .main {
    padding: max(15%, 100px) 3%;
    justify-content: center;
    background-image: url("@/static/destination/background-destination-tablet.jpg");
  }
  .page-content {
    grid-template-columns: 1fr;
    padding-top: 3rem;
  }

  .page-menu span {
    margin: 0 1rem;
  }

  .item-img {
    justify-content: center;
  }

  .item-description {
    text-align: center;
  }

  .item-content {
    padding: 0 10%;
    align-items: center;
  }

  .item-info {
    justify-content: space-around;
    width: 100%;
  }

  @media (max-width: 500px) {
    .page-title {
      font-size: 0.7rem;
      align-self: center;
    }

    .item-img {
      width: 80%;
      justify-content: center;
      margin: 0 auto;
    }

    .item-info {
      flex-direction: column;
      align-items: center;
    }
    .item-distance {
      margin: 0 0 2rem 0;
    }

    .item-distance, .item-travel {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  }
}
</style>
