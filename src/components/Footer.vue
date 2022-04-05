v<template>
  <footer v-if="isMobile()" class="mobile">

  </footer>


  <footer v-else>
    <div class="xiao"></div>
    <div class="footer">
      <div class="call">Связь</div>
      <img class="underline" src="@/assets/call-underground.png">
      <div class="gidro" @click="GoVk"></div>
    </div>
  </footer>
</template>

<script>
import GalleryBlock from "./GalleryBlock.vue";

export default {
  name: "Footer",
  methods: {
    GoVk: function (event) {
      console.log(event)
      window.location = 'https://vk.com/kakoy_yura_uspakoysa';
    },
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

footer.mobile {
  width: 100vw;
  height: 30vw;
  position: absolute;
  top: 0;
  background-color: #2c3e50;
}








footer {
  width: 100vw;
  height: 30vw;
  /*background: #2e012f;*/
}

.footer {
  display: flex;
  height: 100%;
  position: absolute;
  width: 100%;
  margin-top: auto;
  background-size: cover;
  align-items: flex-end;
}

.call {
  position: absolute;
  margin: 0 0 2% 2%;
  font-size: 2vw;
}
.call, .underline {
  z-index: 10;
}
.underline {
  position: absolute;
  margin: 0 0 1.8% 1.7%;
  object-fit: cover;
  width: 7%;
  height: 1.3%;
}

.gidro {
  position: absolute;
  margin: 0 0 0.8% 9%;
  object-fit: cover;
  width: 5%;
  background: url("../assets/vk-nolighter.png") no-repeat center center;
  background-size: cover;
  cursor: pointer;
  width: 5%;
  height: 16%;
  transition: all 0.9s;
}

.gidro:hover {
  background: url("../assets/vk-lighter.png") no-repeat center center;
  background-size: cover;
  transition: all 0.9s;
}

.xiao {
  position: absolute;
  width: 100%;
  height: 100%;
  bottom: 0%;

  background: url("../assets/xiao_bg.png");
  background-size: cover;
}
</style>