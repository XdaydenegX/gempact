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
      <details> <!-- v-for-->
        <summary>
          <div class="gallery-char">
            <div class="element gidro"></div>
            Мона
            <img class="char-img" src=../assets/char/mona.png>
          </div>
        </summary>
        <div class="char-story">
          <h1 class="char-name">Мона</h1>
          <img class="char-elem" src=../assets/gidro-hover.png>
          <img class="char-photo" src="../assets/char/char-info/mona-summary.png">
          <div class="rarity">
            <div class="star">&#10022; &#10022; &#10022; &#10022; &#10022;</div>
          </div>
          <div class="char-info"></div>
          <div class="char-annotation"></div>
        </div>
      </details>
    </div>
    <h1>Coming soon...</h1>
  </main>
</template>

<style>
@media (min-width: 1024px) {
  h1 {
    text-align: center;
  }
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
  margin-bottom: 0%;
  /*margin-top: 15%;*/
}

button {
  background: #FFCF0D;
  border-radius: 20px;
  font-family: "TT_Skip-E";
  position: absolute;
  left: 60%;
  height: 103px;
  top: 0%;
  border: 0;
  font-size: x-large;
  width: 15%;
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

.gallery-char:hover {
  background: url("../assets/mondshtat-bg.png");
  background-position: 0 center;
  border: 20px solid rgba(18, 0, 36, 0.9);
  transition: all 0.9s;
  text-shadow: 4px 4px 25px #000000;
}
.gallery-char:hover .char-img {
  transform: scale(2) translateY(17%);
  transition: all 0.9s;
}

.gallery-char:hover .element.gidro {
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
.gidro {
  background-image: url("../assets/opacity/gidro-elem.png");
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
  width: 14%;
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
</style>
