<template>

  <header v-if="isMobile()" class="mobile">
    <img src="../assets/mobile/icon-mobile.png" class="icon" onclick="window.location = '/'">
    <div class="nav" v-if="home">
      <a @click="scrollTo('card-1', 'mobile')" >
        <img class="gli" src="../assets/mobile/gli.png">
      </a>
      <a @click="scrollTo('card-2', 'mobile')">
        <img class="sqi" src="../assets/mobile/sqi.png">
      </a>
      <a @click="scrollTo('card-3', 'mobile')">
        <img class="wi" src="../assets/mobile/wi.png" @click="scrollTo('card-3')">
      </a>
    </div>
    <div class="nav" v-else-if="gallery">
      <a @click="scrollTo('mondshtat-scroll', 'mobile')" >
        <img class="char-check" src="../assets/mobile/mondshtat-header-logo.png">
      </a>
      <a @click="scrollTo('liyue-scroll', 'mobile')">
        <img class="char-check" src="../assets/mobile/liyue-header-logo.png">
      </a>
      <a @click="scrollTo('inadzuma-scroll', 'mobile')">
        <img class="char-check" src="../assets/mobile/inadzuma-header-logo.png" @click="scrollTo('card-3')">
      </a>
    </div>
  </header>

  <header v-else>
    <div class="gp-bg" onclick="window.location = '/'">
      <div class="sitename">Gempact</div>
    </div>
    <div id="nav" v-if="home">
        <a @click="scrollTo('card-1')">Галерея персонажей</a>
        <a @click="scrollTo('card-2')">Подбор отрядов</a>
        <a @click="scrollTo('card-3')">Оружие</a>
    </div>
    <div id="nav" v-else-if="gallery">
      <a @click="scrollTo('mondshtat-scroll')">Мондштадт</a>
      <a @click="scrollTo('liyue-scroll')">Ли Юэ</a>
      <a @click="scrollTo('inadzuma-scroll')">Инадзума</a>
    </div>
  </header>

</template>

<script>

export default {
  name: "Header",

  methods: {
    scrollTo(el, mode='desktop') {
      console.log('click')
      if (mode == 'desktop') {
        window.scrollBy({
          top: document.getElementById(el).getBoundingClientRect().top - document.getElementsByTagName("header")[0].offsetHeight,
          behavior: 'smooth'
        })
      }

      else {
        document.getElementById(el).scrollIntoView({behavior: "smooth", block: "start", inline: "nearest"})
      }
    },
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true
      } else {
        return false
      }
    },
    },
    data() {
      return {
        home: window.location.pathname == '/' ? true : false,
        ifScroll: false,
        gallery: window.location.pathname == '/gallery' ? true : false
      }
    },

  }

</script>

<style scoped>

header.mobile {
  background: linear-gradient(180deg, rgba(92, 43, 142, 0.5) 0%, rgba(0, 0, 0, 0) 100%), url("@/assets/mobile/header-mobile.png");
  width: 100%;
  height: 178px;
  background-size: cover;
  left: 0px;
  top: 0px;
  background-repeat: no-repeat;
}

header.mobile.scroll {
  top: -50%;
}

.icon {
  object-fit: contain;
  height: 70%;
  width: 100%;
  top: 2%;
}

header.mobile a {
  display: flex;
  align-self: center;
  position: relative;
  cursor: pointer;
  width: 14%;
  justify-content: center;
}

.nav {
  height: 18%;
  width: 100%;
  display: flex;
  position: absolute;
  bottom: 5%;
  justify-content: space-evenly;
}

.gli, .sqi, .wi {
  object-fit: cover;
  width: 80%;
}
.char-check {
  object-fit: cover;
  width: 70%;
  background-color: #FFCF0D;
  border-radius: 10vw;
}






header {
  width: 100vw;
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

@media (max-width: 1440px) {
  header {
    height: 12.5vh;
  }
}


</style>