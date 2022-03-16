<script setup>
</script>
<template>
  <main>
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
  computed: {
    list: function () {
      var list = ["Hello world"];
      for (let i = 0; i < 1000; i++) {
        list.push("Hello world");
      }
      return list;
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
