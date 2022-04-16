<template>
  <footer v-if="isMobile()" class="mobile">
    <img src="../assets/mobile/bennet.png">
    <hr>
    <div class="ante">
      <img src="../assets/mobile/icon-mobile.png">
      <div class="needflex">
        <div class="call-mobile">Связь</div>
        <img class="underline-mobile" src="@/assets/call-underground.png">
        <div class="gidro-mobile" @click="GoVk"></div>
        <span class="footer-site-name-mobile">Gempact</span>
        <span class="footer-site-age-mobile">2022</span>
      </div>
    </div>
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
  height: 20vh;
  background-color: #3D1C5F;
  display: flex;
  bottom: 0;
  transition: all 0.9s;
}

footer.mobile img {
  width: 41.5%;
}
footer.mobile hr {
  height: 90%;
  top: 1vh;
  border-color: #2A0054;
  right: 3vw;
}
.ante {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  flex-wrap: nowrap;
  justify-content: space-around;
}
.needflex {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 210px;
}
.underline-mobile {
  position: absolute;
  top: 19px;
  object-fit: cover;
  width: 55px !important;
  left: -2px;
}

.footer-site-name-mobile {
  left: 3vw;
  opacity: 0.8;
}
.footer-site-age-mobile {
  right: 2vw;
  opacity: 0.4;
}
.gidro-mobile {
  background: url("../assets/vk-nolighter.png") no-repeat center center;
  position: absolute;
  margin: 0 0 0 9%;
  object-fit: cover;
  width: 30px;
  height: 30px;
  background-size: cover;
  cursor: pointer;
  left: 8vw;
  bottom: -0.4vh;
}
.gidro-mobile:hover {
  background: url("../assets/vk-lighter.png") no-repeat center center;
  background-size: cover;
  transition: all 0.9s;
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