<script setup>
</script>
<template>

<main v-if="isMobile()" class="mobile">
  <div class="q" @click="toggleElement('q')" style="opacity: 1;">?</div>
  <div class="ant" v-show="isElVisible">Данный сайт поможет новичкам в игре<br>Genshin Impact собрать отряд из<br>определленных
    персонажей,<br>продемонстрирует их<br>способности и материалы для прокачки.<br><br>
    Часть информации будет субъективно<br>личным мнением создателей сайта
  </div>
  <GalleryBlock></GalleryBlock>
  <h1 class="cs-mobile">Coming soon...</h1>
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
      console.log(document.getElementsByClassName(el)[0].style.opacity);
      if (document.getElementsByClassName(el)[0].style.opacity == 1 || null) {
        document.getElementsByClassName(el)[0].setAttribute("style", "opacity: 0.5;")
        document.querySelector('.card-mobile').setAttribute('style', "margin-top: 35vw;")

      }
      else  {
        document.getElementsByClassName(el)[0].setAttribute("style", "opacity: 1;")
        document.querySelector('.card-mobile').setAttribute('style', "margin-top: 0;")

      }
      document.getElementsByClassName(el)[0].style.opacity = (el.style.opacity == 0.5) ? 1: 0.5;
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
  z-index: 5;
  opacity: 1;
}

main.mobile .ant {
  width: 96%;
  left: 2%;
  text-align: center;
  height: 170px;
  opacity: 1;
  position: absolute;
  top: -0.5%;
  background: rgba(18, 0, 36, 0.6);
  border: 3px solid rgba(61, 28, 95, 0.6);
  transition: all 0.9s ease-in-out;
  animation: fadeIn 1s ease-in-out;
  display: flex;
  font-size: 3vw;
  justify-content: center;
  align-items: center;
  color: rgba(255, 255, 255, 0.55);
}

@keyframes fadeIn {
0% {
  opacity: 0;
}
  100% {
    opacity: 1;
  }
}


.ant:disabled {
  margin-top: 20vw;
}

GalleryBlock {
  transition: all 2s ease-in-out;
  animation: fadeOut 2s ease-in-out;
}
@keyframes fadeOut {
  0% {
    margin-top: 0;
  }
  100% {
    margin-top: 20vw;
  }
}
 .cs-mobile{
  font-size: 2rem;
   margin-top: 10vh;
   margin-bottom: 30vh;
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
