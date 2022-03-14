<template>
  <div class="main">
    <section>
      <h2>so, you want to travel to</h2>
      <h1>space</h1>
      <p>
        Let’s face it; if you want to go to space, you might as well genuinely
        go to outer space and not hover kind of on the edge of it. Well sit
        back, and relax because we’ll give you a truly out of this world
        experience!
      </p>
    </section>
    <aside>
      <div class="explore">explore</div>
    </aside>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
};
</script>

<style scoped>
.main {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  background-image: url("@/static/home/background-home-desktop.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  padding: 8% 10%;
}

section,
aside {
  width: 40%;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

section {
  align-items: flex-start;
}

section h1 {
  font-size: clamp(80px, 15vw, 150px);
  text-transform: uppercase;
  font-family: "bellefair";
}

section h2 {
  font-size: clamp(12px, 2vw, 28px);
  text-transform: uppercase;
  font-family: "barlow";
  letter-spacing: 4.75px;
  color: var(--light);
}

section p {
  text-transform: initial;
  color: var(--light);
  font-size: clamp(0.7rem, 3vw, 1rem);
  font-weight: 300;
  line-height: 180%;
}

.explore {
  position: relative;
  background-color: var(--white);
  color: var(--dark);
  width: clamp(180px, 50vw, 250px);
  border-radius: 50%;
  aspect-ratio: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.8rem;
  text-transform: uppercase;
  font-family: "bellefair";
  cursor: pointer;
}

.explore::before {
  display: block;
  width: clamp(180px, 50vw, 250px);
  border-radius: 50%;
  aspect-ratio: 1;
  content: "";
  transition: all 0.9s ease;
  position: absolute;
  background-color: rgba(255, 255, 255, 0.151);
}

.explore:hover::before {
  transform: scale(1.5);
}

@media (max-width: 900px) {
  .main {
    background-image: url("@/static/home/background-home-tablet.jpg");
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
  }
  section {
    align-items: center;
  }
  section,
  aside {
    width: 70%;
    align-items: center;
  }

  section p,
  h2 {
    text-align: center;
  }
}

@media (max-width: 500px) {
  .main {
    background-image: url("@/static/home/background-home-mobile.jpg");
    padding: 10% 5%;
  }
  section,
  aside {
    width: 100%;
  }
}
</style>
