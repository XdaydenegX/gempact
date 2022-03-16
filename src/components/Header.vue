<template>
  <header>
    <div class="gp-bg" onclick="window.location = '/'">
      <div class="sitename">Gempact</div>
    </div>
    <div id="nav" v-if="home">
      <!--  <router-link to="/">Home</router-link> |-->
      <!--  <router-link to="/about">About</router-link>-->
        <a @click="scrollTo('card-1')">Галерея персонажей</a>
        <a @click="scrollTo('card-2')">Подбор отрядов</a>
        <a @click="scrollTo('card-3')">Оружие</a>

    </div>
  </header>

</template>

<script>
export default {
  name: "Header",
  methods: {
    scrollTo(el) {

      window.scrollBy({
        top: document.getElementById(el).getBoundingClientRect().top - 150,
        behavior: 'smooth'
      })
    }
  },
  data() {
    return {
      home: window.location.pathname == '/' ? true : false,
    }
  }

}

</script>

<style scoped>

header {
  width: 100%;
  height: 16.5vh;
  background: linear-gradient(
      0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)), url("@/assets/header-bg.png");
  background-size: cover;
  background-position: center center;
  color: #FFFFFF;
  position: fixed;
  display: flex;
  z-index: 50;
  flex-direction: row;
}

#nav {
  height: 100%;
  width: 50%;
  display: flex;
  left: calc(50% - 50% / 2);
  position: absolute;
  justify-content: space-evenly;
}
a {
  display: flex;
  align-self: center;
  position: relative;
  cursor: pointer;
  font-size: x-large;
}

@font-face {
  font-family: "TT_Skip-E";
  src: url(../fonts/genshin.ttf);
}



.gp-bg {
  position: absolute;
  z-index: 3;
  width: 17vw;
  background: radial-gradient(50% 50% at 50% 50%, #FEF9CC 0%, rgba(255, 255, 255, 0) 100%);
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.5);
  cursor: pointer;
  height: 100%;
  bottom: 5%;
  font-size: 2.7vw;
  justify-content: center;
  display: flex;
  align-items: center;
}


</style>