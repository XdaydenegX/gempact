<template>
  <main>
    <div class="annotation">Данный сайт поможет новичкам в игре Genshin Impact собрать отряд из определленных<br>
      персонажей, продемонстрирует их способности и материалы для прокачки.
      <br>
      <br>
      Часть информации будет субъективно личным мнением создателей сайта</div>
    <button onclick="window.location = '/' ">Вернуться назад</button>
    <div class="gallery-container">
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
          <button @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <div class="gallery-container">
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
          <button @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <div class="gallery-container">
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
          <button @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <h1>Coming soon...</h1>
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
  },
  name: "GalleryView",
  data: function () {
    return {
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

.element.crio {
  background: url("../assets/opacity/crio-elem.png");
  opacity: 0.6;
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
  font-size: 1.45vw;
  position: absolute;
  top: 325px;
  left: 17rem;
  width: 74%;
}

.citation {
  position: relative;
  font-size: x-large;
  display: flex;
  text-align: center;
  margin-top: 2vw;
  justify-content: center;
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
}
</style>
