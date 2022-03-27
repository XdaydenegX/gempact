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
      <details v-for="item in char" v-bind="{id: item.id}"> <!-- v-for-->
        <summary>
          <div class="gallery-char" v-bind:class="[item.bg]">
            <div class="element" v-bind:class="[item.elem]"></div>
            {{item.name}}
            <img class="char-img" :src="`src/assets/char/${item.img}.png`">
          </div>
        </summary>
        <div class="char-story">
          <h1 class="char-name">Мона</h1>
          <div class="things">
            <img class="char-elem" src="../assets/gidro-hover.png">
            <img class="char-photo" src="../assets/char/char-info/mona-summary.png">
            <div class="rarity">
              <div class="star">&#10022; &#10022; &#10022; &#10022; &#10022;</div>
            </div>
          </div>
          <p class="citation">Судьбу нельзя изменить, ей нельзя противиться, её можно только принять.<br>Поэтому она называется судьбой.</p>
          <div class="char-info">Мона Мегистус  —  таинственный астролог без гроша в кармане. Ее внешний вид довольно<br>
            экстравагантен, но видимо он позволяет ей лучше сливаться со своей Гидро стихией.
            <br>Анимация ее способностей выше всяких похвал, да и сами способности будут полезны
            <br>большинству путешественников. И не поскупитесь заказать ей обед ведь астролог это не
            <br>художник он не должен быть голоден, тем более такая милашка.</div>
          <div class="char-arts">
            <img src=../assets/char/char-info/char-art-1.jpg>
            <img src=../assets/char/char-info/char-art-2.jpg>
            <img src=../assets/char/char-info/char-art-3.jpg>
            <img src=../assets/char/char-info/char-gif.gif>
          </div>
          <div class="char-annotation">
            <span>Характеристики персонажа можно будет<br>
              увидеть в подборе отрядов при выборе<br>
              этого персонажа</span>
          </div>
          <button @click="CloseDetails($event.target)" class="char-btn">Скрыть</button>
        </div>
      </details>
    </div>
    <h1>Coming soon...</h1>
  </main>
</template>


<script>

export default {
  methods: {
    CloseDetails: function(el) {
      console.log(el);
      window.scrollBy({
        top: el.parentElement.parentElement.getBoundingClientRect().top - document.getElementsByTagName("header")[0].offsetHeight - 20,
        // behavior: "smooth"
      })
      el.parentElement.parentElement.removeAttribute("open");
    }
  },
  name: "GalleryView",
  data: function() {
    return {
      char: [ {id: "char-1",  bg: "mondshtat", elem: "gidro", name: "Мона", img: "mona", eleminfo: "../assets/gidro-hover.png",
            star: "&#10022; &#10022; &#10022; &#10022; &#10022;", info: "Мона Мегистус  —  таинственный астролог без гроша в кармане. Ее внешний вид довольно\n" +
            "экстравагантен, но видимо он позволяет ей лучше сливаться со своей Гидро стихией.\n" +
            "Анимация ее способностей выше всяких похвал, да и сами способности будут полезны\n" +
            "большинству путешественников. И не поскупитесь заказать ей обед ведь астролог это не\n" +
            "художник он не должен быть голоден, тем более такая милашка.", citation: "Судьбу нельзя изменить, ей нельзя противиться, её можно только принять.\n" +
            "Поэтому она называется судьбой.", charphotoone: "../assets/char/char-info/char-art-1.jpg", charphototwo: "../assets/char/char-info/char-art-2.jpg",
            charphotothree: "../assets/char/char-info/char-art-3.jpg", chargif: "../assets/char/char-info/char-gif.gif",
            charspan: "Характеристики персонажа можно будет\n" + "увидеть в подборе отрядов при выборе\n" + "этого персонажа"}]
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
  border: 20px solid rgba(18, 0, 36, 0.9);
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




.char-img {
  right: 8%;
  position: absolute;
  width: 24%;
  transition: all 0.9s;
}

details {
  margin: auto;
  width: 80%;
  margin-bottom: 2%;
  transition: all 0.9s;
}
details[open] {
  margin-bottom: 30%;
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
  font-size: 1.2vw;
  position: absolute;
  top: 17rem;
  left: 20%;
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

.char-arts img {
  margin-bottom: 20px;
}

.char-annotation {
  display: flex;
  justify-content: center;
  text-align: center;
  opacity: 0.6;
  margin-top: 30px;
}

.char-btn {
  position: relative;
  margin-left: 20%;
}
</style>
