<script setup>
import { RouterLink, RouterView } from 'vue-router';
</script>

<template>
<Header></Header>
  <RouterView />
  <Footer></Footer>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

export default  {
  components: {
    Header,
    Footer
  }
}
</script>

<style>
@import '@/assets/base.css';


@font-face {
  font-family: 'TT_Skip-E';
  src: url("./fonts/genshin.ttf") format('truetype');
  font-weight: normal;
  font-style: normal;
}


html,
body,
#app {
  margin: 0;
  padding: 0;
  min-height: 100%;
  background: linear-gradient(120deg, #11001a, #29013f, #2e012f);
  font-family: "TT_Skip-E";
  display: flex;
  flex-direction: column;
  color: white;
  overflow-x: hidden;
  height: auto !important;
}
main {
  position: relative;
  width: 100%;
  top: 15%;
  height: 100%;
  flex-direction: column;
  display: flex;
  /* justify-self: center; */
  /* align-self: center; */
  /* align-items: center; */
  justify-content: center;
  flex: 1 1 auto;
  margin-top: 10%;
  margin-bottom: 15%;
}
</style>
