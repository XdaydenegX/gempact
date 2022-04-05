<script setup>
</script>
<template>

<main v-if="isMobile()" class="mobile">
  <div class="q" @click="toggleElement(this.$el)">?</div>
  <div class="ant" v-show="isElVisible">dddddd</div>
</main>



  <main v-else>
    <div class="annotation">Данный сайт поможет новичкам в игре Genshin Impact собрать отряд из определленных<br>
      персонажей, продемонстрирует их способности и материалы для прокачки.
      <br>
      <br>
      Часть информации будет субъективно личным мнением создателей сайта</div>
    <GalleryBlock></GalleryBlock>
    <h1>Coming soon...</h1>
  </main>

</template>


<script>

import GalleryBlock from "../components/GalleryBlock.vue";

export default {
  name: "Home",
  components: {
    GalleryBlock
  },
  methods: {
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true
      } else {
        return false
      }
    },
    toggleElement(el) {
      this.isElVisible = !this.isElVisible
      el.style.opacity = (el.style.opacity == 0.5) ? 1: 0.5;
    }
  },
  data: () => {
    return {
      isElVisible: false
    }
  }
}
</script>
<style scoped>

body{
  height: 100%;
}

main.mobile .q {
  height: 5.5%;
  width: 10%;
  margin-left: 15px;
  background-color: #FFCC00;
  border-radius: 50px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  font-size: 6vw;
  transition: all 0.9s;
  color: black;
  z-index:5;
}

main.mobile .ant {
  width: 92%;
  left: 2%;
  text-align: center;
  height: 170px;
  opacity: 1;
  position: absolute;
  top: -2%;
  background: rgba(18, 0, 36, 0.6);
  border: 3px solid rgba(61, 28, 95, 0.6);
  transition: all 0.9s ease-in-out;
  animation: fadeIn-9ea40744 1s ease-in-out;
}
@keyframes fadeIn {
0% {
  opacity: 0;
}
  100% {
    opacity: 1;
  }
}



.annotation {
  position: relative;
  left: 1%;
  font-size: 1.2rem;
  opacity: 0.4;
  width: max-content;
}

h1 {
  text-align: center;
  font-size: xxx-large;
  opacity: 0.6;
  margin-bottom: 15%;
  margin-top: 15%;
}

</style>
