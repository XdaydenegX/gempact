<script setup>
</script>
<template>
<main v-if="isMobile()">
<h1>Mobile</h1>
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
    }
  }
}
</script>
<style scoped>


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
