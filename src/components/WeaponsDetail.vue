<template>
  <div class="weapon-container" v-for="item in weapons" v-bind:id="{id: item.id}" v-if="is_show">
    <div class="weapon-list">
      <div class="weapon-photo" v-bind:class="[item.rare]">
        <img :src="GetPathToImage(item.bg)">
      </div>
      <div class="weapon-info">
        <h1>{{item.name}}</h1>
        <br>
        <h2>{{item.stars}}</h2>
      </div>
      <div class="circle-menu-button">
        <hr class="hr-1">
        <hr class="hr-2">
      </div>
    </div>
  </div>
</template>

<script>
export default {
name: "WeaponsDetail",
  props: ['weapons', 'is_show'],
  methods: {
    GetPathToImage: function (img) {
      return new URL(`../assets/${img}`, import.meta.url).href;
    },
  }
}

</script>

<style scoped>

</style>