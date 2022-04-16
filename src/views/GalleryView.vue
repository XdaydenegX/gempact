<template>
  <main>
    <div class="mobile" v-if="isMobile()">
      <div class="q" @click="toggleElement('q')" style="opacity: 1;">?</div>
      <div class="ant" v-show="isElVisible">Данный сайт поможет новичкам в игре<br>Genshin Impact собрать отряд из<br>определленных
        персонажей,<br>продемонстрирует их<br>способности и материалы для прокачки.<br><br>
        Часть информации будет субъективно<br>личным мнением создателей сайта
      </div>
    </div>
    <div class="annotation" v-else>Данный сайт поможет новичкам в игре Genshin Impact собрать отряд из определленных<br>
      персонажей, продемонстрирует их способности и материалы для прокачки.
      <br>
      <br>
      Часть информации будет субъективно личным мнением создателей сайта
    </div>
    <br>
    <button v-if="isMobile()" v-show="isReturnButton" class="go-to-back" onclick="window.location = '/' ">
      <img class="backarrow" src="../assets/mobile/backarrow.png">
    </button>
    <button onclick="window.location = '/' " v-else>Вернуться назад</button>
    <div class="gallery-container" id="mondshtat-scroll">
      <h1>Мондштадт</h1>
      <details v-for="item in mondshtat" v-bind="{id: item.id}"> <!-- v-for-->
        <summary>
          <div class="gallery-char" v-bind:class="[item.bg]">
            <div class="element" v-bind:class="[item.elem]"></div>
            {{item.name}}
            <img class="char-img" :src="GetPathToImage(item.img)">
          </div>
        </summary>
        <div class="char-story">
          <h1 class="char-name">{{item.name}}</h1>
          <div class="things">
            <img class="char-elem" :src="GetPathToImage(item.eleminfo)">
            <img class="char-photo" :src="GetPathToImage(item.charphotosummary)">
            <div class="rarity">
              <div class="star">{{item.star}}</div>
            </div>
          </div>
          <i><p class="citation">{{item.citation}}</p></i>
          <div class="char-info">{{item.info}}</div>
          <div class="char-arts" v-for="photo in item.photo">
            <img :src="GetPathToImage(photo)">
          </div>
          <div class="char-annotation">
            <span>{{item.charspan}}</span>
          </div>
          <button v-if="isMobile()" v-show="isCloseButton" @click="CloseDetails($event.target)" class="close-btn">×</button>
          <button v-else @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <div class="gallery-container" id="liyue-scroll">
      <h1>Ли Юэ</h1>
      <details v-for="item in liyue" v-bind="{id: item.id}"> <!-- v-for-->
        <summary>
          <div class="gallery-char" v-bind:class="[item.bg]">
            <div class="element" v-bind:class="[item.elem]"></div>
            {{item.name}}
            <img class="char-img" :src="GetPathToImage(item.img)">
          </div>
        </summary>
        <div class="char-story">
          <h1 class="char-name">{{item.name}}</h1>
          <div class="things">
            <img class="char-elem" :src="GetPathToImage(item.eleminfo)">
            <img class="char-photo" :src="GetPathToImage(item.charphotosummary)">
            <div class="rarity">
              <div class="star">{{item.star}}</div>
            </div>
          </div>
          <i><p class="citation">{{item.citation}}</p></i>
          <div class="char-info">{{item.info}}</div>
          <div class="char-arts" v-for="photo in item.photo">
            <img :src="GetPathToImage(photo)">
          </div>
          <div class="char-annotation">
            <span>{{item.charspan}}</span>
          </div>
          <button v-if="isMobile()" v-show="isCloseButton" @click="CloseDetails($event.target)" class="close-btn">×</button>
          <button v-else @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <div class="gallery-container" id="inadzuma-scroll">
      <h1>Инадзума</h1>
      <details v-for="item in inadzuma" v-bind="{id: item.id}"> <!-- v-for-->
        <summary>
          <div class="gallery-char" v-bind:class="[item.bg]">
            <div class="element" v-bind:class="[item.elem]"></div>
            {{item.name}}
            <img class="char-img" :src="GetPathToImage(item.img)">
          </div>
        </summary>
        <div class="char-story">
          <h1 class="char-name">{{item.name}}</h1>
          <div class="things">
            <img class="char-elem" :src="GetPathToImage(item.eleminfo)">
            <img class="char-photo" :src="GetPathToImage(item.charphotosummary)">
            <div class="rarity">
              <div class="star">{{item.star}}</div>
            </div>
          </div>
          <i><p class="citation">{{item.citation}}</p></i>
          <div class="char-info">{{item.info}}</div>
          <div class="char-arts" v-for="photo in item.photo">
            <img :src="GetPathToImage(photo)">
          </div>
          <div class="char-annotation">
            <span>{{item.charspan}}</span>
          </div>
          <button v-if="isMobile()" v-show="isCloseButton" @click="CloseDetails($event.target)" class="close-btn">×</button>
          <button v-else @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <h1 class="cska">Coming soon...</h1>
  </main>
</template>


<script>
import  mondshtat from '../data/mondshtat.json'
import liyue from '../data/liyue.json'
import inadzuma from '../data/inadzuma.json'
export default {
  methods: {
    CloseDetails: function (el) {
      window.scrollBy({
        top: el.parentElement.parentElement.getBoundingClientRect().top - document.getElementsByTagName("header")[0].offsetHeight - 20,
        // behavior: "smooth"
      })
      el.parentElement.parentElement.removeAttribute("open");
    },
    GetPathToImage: function (img) {
      return new URL(`../assets/${img}`, import.meta.url).href;
    },
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
        document.querySelector('.gallery-container').setAttribute('style', "margin-top: 35vw;")
        document.querySelector('.go-to-back').setAttribute('style', "margin-top: 35vw; margin-bottom: 35vw;")
      }
      else  {
        document.getElementsByClassName(el)[0].setAttribute("style", "opacity: 1;")
        document.querySelector('.gallery-container').setAttribute('style', "margin-top: 10vw;")
        document.querySelector('.go-to-back').setAttribute('style', "margin-top: 0;")
      }
      document.getElementsByClassName(el)[0].style.opacity = (el.style.opacity == 0.5) ? 1: 0.5;
    },
  },
  name: "GalleryView",
  data: function () {
    return {
      isElVisible: false,
      isReturnButton: true,
      isCloseButton: true,
      mondshtat: mondshtat,
      liyue: liyue,
      inadzuma: inadzuma
    }
  },
}
</script>


<style>
@media (min-width: 1024px) {
  h1 {
    text-align: center;
  }
}

.annotation {
  position: relative;
  left: 1%;
  font-size: 1vw;
  opacity: 0.4;
  width: max-content;
  margin-bottom: 10%;
}

h1 {
  text-align: center;
  font-size: xxx-large;
  opacity: 0.6;
  margin-bottom: 0%;
  /*margin-top: 15%;*/
}

button {
  background: #FFCF0D;
  border-radius: 20px;
  font-family: "TT_Skip-E";
  position: absolute;
  left: 60%;
  height: 5vw;
  top: 0%;
  border: 0;
  font-size: 1.4vw;
  width: 14vw;
  cursor: pointer;
  color: #341C00;
}

.gallery-char {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url("../assets/mondshtat-bg.png");
  width: 100%;
  height: 10.6vw;
  display: flex;
  padding: 0;
  overflow: hidden;
  background-position: center center;
  justify-content: center;
  align-items: center;
  font-size: xxx-large;
  transition: all 0.9s;
  border-radius: 20px;
  cursor: pointer;
}

.gallery-char:before, .gallery-char:after {
  transition: all 0.9s;
}

details summary::-webkit-details-marker {
  display: none;
}
/* Убираем стандартный маркер Firefox */
details > summary {
  list-style: none;
}



.gallery-char:hover.mondshtat {
  background: url("../assets/mondshtat-bg.png");
  background-position: 0 center;
  border: 10px solid rgba(0, 7, 36, 0.9);
  transition: all 0.9s;
  text-shadow: 4px 4px 25px #000000;
}
.gallery-char:hover.mondshtat .char-img {
  transform: scale(2) translateY(17%);
  transition: all 0.9s;
}

.gallery-char:hover.mondshtat .element.gidro {
  opacity: 1;
  background: url("../assets/gidro-hover.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.mondshtat .element.geo {
  opacity: 1;
  background: url("../assets/gidro-hover.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}


.gallery-char:hover.liyue {
  background: url("../assets/liyue-bg.jpg");
  background-position: 0 center;
  border: 10px solid rgba(36, 11, 0, 0.9);
  transition: all 0.9s;
  text-shadow: 4px 4px 25px #000000;
}
.gallery-char.liyue {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url("../assets/liyue-bg.jpg");

  background-position: center center;

}
.gallery-char:hover.liyue .char-img {
  transform: scale(2) translateY(17%);
  transition: all 0.9s;
}

.gallery-char:hover.inadzuma {
  background: url("../assets/inadzuma-bg.jpg");
  background-position: 0 center;
  border: 10px solid rgb(26, 0, 40);
  transition: all 0.9s;
  text-shadow: 4px 4px 25px #000000;
}
.gallery-char.inadzuma {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url("../assets/inadzuma-bg.jpg");

  background-position: center center;

}
.gallery-char:hover.inadzuma .char-img {
  transform: scale(2) translateY(17%);
  transition: all 0.9s;
}

.gallery-char:hover.liyue .element.gidro {
  opacity: 1;
  background: url("../assets/gidro-hover.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}


.element {
  object-fit: cover;
  display: flex;
  width: 100px;
  left: 5%;
  background-position: center center;
  background-size: cover;
  height: 95px;
  position: absolute;
  justify-self: flex-start;
  opacity: 0.5;
  transition: all 0.9s;
}
.element.gidro {
  background: url("../assets/opacity/gidro-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.mondshtat .element.piro {
  opacity: 1;
  background: url("../assets/elem/piro.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.element.piro {
  background: url("../assets/opacity/piro-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}

.element.geo {
  background: url("../assets/opacity/geo-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.liyue .element.elektro {
  opacity: 1;
  background: url("../assets/elem/elektro.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.liyue .element.geo {
  opacity: 1;
  background: url("../assets/elem/geo.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.liyue .element.crio {
  opacity: 1;
  background: url("../assets/elem/crio.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.element.crio {
  background: url("../assets/opacity/crio-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}


.gallery-char:hover.liyue .element.piro {
  opacity: 1;
  background: url("../assets/elem/piro.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.element.piro {
  background: url("../assets/opacity/piro-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}




.gallery-char:hover.mondshtat .element.elektro {
  opacity: 1;
  background: url("../assets/elem/elektro.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.element.elektro {
  background: url("../assets/opacity/electro-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.mondshtat .element.anemo {
  opacity: 1;
  background: url("../assets/elem/anemo.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.element.anemo  {
  background: url("../assets/opacity/anemo-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.inadzuma .element.crio {
  opacity: 1;
  background: url("../assets/elem/crio.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.gallery-char:hover.inadzuma .element.anemo {
  opacity: 1;
  background: url("../assets/elem/anemo.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}

.element.anemo {
  background: url("../assets/opacity/anemo-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}

.element.crio {
  background: url("../assets/opacity/crio-elem.png");
  opacity: 0.6;
  background-position: center center;
  background-size: cover;
}
.gallery-char:hover.inadzuma .element.elektro {
  opacity: 1;
  background: url("../assets/elem/electro.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}
.gallery-char:hover.inadzuma .element.piro {
  opacity: 1;
  background: url("../assets/elem/piro.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}
.gallery-char:hover.inadzuma .element.geo {
  opacity: 1;
  background: url("../assets/elem/geo.png");
  transition: all 0.9s;
  background-position: center center;
  background-size: cover;
}






.char-img {
  right: 8%;
  position: absolute;
  width: 30%;
  transition: all 0.9s;
}

.char-img {
  right: 8%;
  position: absolute;
  width: 30%;
  transition: all 0.9s;
}

details {
  margin: auto;
  width: 80%;
  margin-bottom: 2%;
  transition: all 0.9s;
}
details[open] {
  margin-bottom: 10%;
  cursor: pointer;
}

details[open] .char-story {
  animation: slide 1s ease-in-out;
}

.char-story {
  width: 100%;
  background: radial-gradient(50% 50% at 50% 50%, rgba(18, 0, 36, 0.9) 0%, rgba(0, 0, 0, 0.9) 100%);
  margin: auto;
  padding: 2%;
  overflow: hidden;
  word-break: break-all;
  border-radius: 10px;
}

.char-name {
  margin-top: 0%;
  opacity: 1;
}

@keyframes slide {
  0%    { opacity: 0; transform:  translate(0, -10px); }
  100%  { opacity: 1; transform:  translate(0, 0); }
}

.char-elem {
  position: relative;
  width: 200px;
  display: flex;
  margin-bottom: 1vw;
}

.rarity {
  position: relative;
  display: flex;
  width: 15%;
  margin: 0;
  justify-content: center;
}

.star {
  color: #ffcb3a;
  font-size: 20px;
  padding-right: 0.25rem;
  text-shadow: 0 0 1px #302508;
}

.char-photo {
  width: 200px;
  height: 300px;
  border-radius: 13px;
  top: 4%;
  position: relative;
}

.rarity {
  width: 200px;
}

.things {

}

.char-info {
  display: flex;
  justify-content: center;
  font-size: 1.3rem;
  position: absolute;
  top: 325px;
  padding-left: 1vw;
  left: calc(50% - 50%/2);
  width: 60%;
}

.citation {
  position: relative;
  font-size: x-large;
  display: flex;
  text-align: center;
  margin-top: 2vw;
  justify-content: center;
  padding-top: 12vh;
}

.char-arts {
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* flex-wrap: wrap; */
  margin-top: 53px;
  align-content: space-between;
  flex-direction: column;
}

.char-arts {
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* flex-wrap: wrap; */
  margin-top: 53px;
  align-content: space-between;
  flex-direction: column;
}

.char-arts img {
  margin-bottom: 20px;
}

.char-annotation {
  display: flex;
  justify-content: center;
  text-align: center;
  opacity: 0.6;
  margin-top: 30px;
  width: 100%;
}
.char-annotation span {
  width: 330px;
}

.char-btn {
  position: relative;
  margin-left: 20%;
}

.char-arts img {
  object-fit: contain;
  width: 1000px;
  height: 500px;
}


.gallery-container {
  margin-bottom: 4vw;
  margin-top: 11vw;
}

.mobile .q {
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

.mobile .ant {
  width: 96%;
  left: 2%;
  text-align: center;
  height: 170px;
  opacity: 1;
  position: absolute;
  top: -2vw;
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

@media (max-width: 1080px) {
  .go-to-back {
    height: 4.5vh;
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
    left: 0;
    top: 11vw;
  }
  h1 {
    font-size: 2rem;
  }
  .gallery-char {
    font-size: 1.2rem;
    border-radius: 20px;
    height: 15vw;
  }
  .gallery-char:hover.mondshtat {
    background: url("../assets/mondshtat-bg.png");
    background-position: 0 center;
    border: 3px solid rgba(0, 7, 36, 0.9);
    transition: all 0.9s;
    text-shadow: 4px 4px 25px #000000;
  }
  .element {
    object-fit: cover;
    display: flex;
    width: 30px;
    left: 6%;
    background-position: center center;
    background-size: cover;
    height: 30px;
    position: absolute;
    justify-self: flex-start;
    opacity: 0.5;
    transition: all 0.9s;
  }
  .char-img {
    right: -4%;
    position: absolute;
    width: 40%;
    transition: all 0.9s;
  }
  .gallery-char:hover.liyue {
    background: url("../assets/liyue-bg.jpg");
    background-position: 0 center;
    border: 3px solid rgba(36, 11, 0, 0.9);
    transition: all 0.9s;
    text-shadow: 4px 4px 25px #000000;
  }
  .gallery-char:hover.inadzuma {
    background: url("../assets/inadzuma-bg.jpg");
    background-position: 0 center;
    border: 3px solid rgb(26, 0, 40);
    transition: all 0.9s;
    text-shadow: 4px 4px 25px #000000;
  }
  .char-story {
    width: 100%;
    background: radial-gradient(50% 50% at 50% 50%, rgba(18, 0, 36, 0.9) 0%, rgba(0, 0, 0, 0.9) 100%);
    margin: auto;
    padding: 2%;
    overflow: hidden;
    word-break: break-all;
    display: flex;
    flex-direction: column;
    align-content: center;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
  }
  .char-info {
    font-size: 3vw;
    position: relative;
    top: 0;
    left: 0;
    width: auto;
  }
  .citation {
    font-size: 0.82rem;
    margin-bottom: 3vw;
  }
  .char-arts img {
    object-fit: contain;
    width: 78vw;
    height: max-content;
  }
  .char-annotation span {
    font-size: 2vw;
    width: 38vw;
  }
  .close-btn {
    position: relative;
    text-align: center;
    left: 33vw;
    bottom: 9vw;
    width: 8vw;
    height: 8vw;
    font-size: 6.8vw;
  }
  .cska {
    margin-bottom: 15vh;
    margin-top: 2vh;
  }
  .gallery-container {
    margin-bottom: 4vw;
    margin-top: 11vw;
    width: 120%;
    right: 10%;
    padding-top: 23vh;
  }

}
@media (max-width: 1024px) {
 char-info {
   display: flex;
   justify-content: center;
   font-size: 1.45vw;
   position: absolute;
   top: 285px;
   left: 15rem;
   width: 63%;
 }
}
@media (max-width: 1440px) {

}


</style>
