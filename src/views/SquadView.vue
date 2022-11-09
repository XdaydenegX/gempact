<template>
  <main v-if="isMobile()">
    <h1 class="mobile">Это страница Отрядов!</h1>
    <p class="mobile">Тут пока что еще ничего нет...</p>
    <span class="mobile">Пожалуйста ожидайте...)</span>
  </main>
  <main v-else>
    <div class="annotation">
      Данный сайт поможет новичкам в игре Genshin Impact собрать отряд из определленных
      <br>
      персонажей, продемонстрирует их способности и материалы для прокачки.
      <br>
      <br>
      Часть информации будет субъективно личным мнением создателей сайта
    </div>
    <br>
    <button onclick="window.location = '/' ">Вернуться назад</button>
    <div class="upper">
      <div class="squad-container">
        <div class="char-card-position">
          <div class="plus" @click="ShowCharCase()">+</div>
        </div>
        <div class="char-card-position">
          <div class="plus" @click="ShowCharCase()">+</div>
        </div>
        <div class="char-card-position">
          <div class="plus" @click="ShowCharCase()">+</div>
        </div>
        <div class="char-card-position">
          <div class="plus" @click="ShowCharCase()">+</div>
        </div>
        <div class="check" @click="CalculatePercentage()">✔</div>
      </div>
      <div class="purcent">???</div>
    </div>
    <div class="char-case" v-if="CharCase === true" >
      <div class="case" v-for="item in mondshtat" v-bind="{id: item.id}" @click="SetChar($event.target.parentElement.parentElement, charlist)">
        <div class="char-card" v-bind:class="[item.elem]">
          <img class="char-photo-card" :src="GetPathToImage(item.cardphoto)">
        </div>
        <p>{{item.name}}</p>
      </div>
      <div class="case" v-for="item in liyue" v-bind="{id: item.id}" @click="SetChar($event.target.parentElement.parentElement, charlist)">
        <div class="char-card" v-bind:class="[item.elem]">
          <img class="char-photo-card" :src="GetPathToImage(item.cardphoto)">
        </div>
        <p>{{item.name}}</p>
      </div>
      <div class="case" v-for="item in inadzuma" v-bind="{id: item.id}" @click="SetChar($event.target.parentElement.parentElement, charlist)">
        <div class="char-card" v-bind:class="[item.elem]">
          <img class="char-photo-card" :src="GetPathToImage(item.cardphoto)">
        </div>
        <p>{{item.name}}</p>
      </div>
    </div>
    <div class="xar-box" v-show="XarXbox" v-for="item in charcaselist" v-bind="{id: item.id}" v-bind:class="[item.elem]">
      <img class="char-box" :src="GetPathToImage(item.photo)">
      <div class="informasa">
        <h1 class="xar-name">{{item.name}}</h1>
        <h1 class="xar-ratting" v-bind:class="[item['ratings-color']]">{{item.ratings}}</h1>
        <div class="xar-ch">
          <h1 class="xar-weapon">Оружие: {{item.weapoon}}</h1>
        </div>
      </div>
      <details>
        <summary @click="Mama($event.target)">
          Подробнее
        </summary>
        <div class="isesc">
          <p class="pluses">Сильные стороны персонажа {{item.name}}</p>
          <div class="plus-minus">
            <p class="plusess">
              {{item.pluses['pl1']}}<br><br>
              {{item.pluses['pl2']}}<br><br>
              {{item.pluses['pl3']}}</p>
            <img class="chibi-plus" :src="GetPathToImage(item.pluses['chibpl'])">
          </div>
          <p class="minuses">Слабые стороны персонажа {{item.name}}</p>
          <div class="plus-minus">
            <p class="minusess">
              {{item.minuses['min1']}}<br><br>
              {{item.minuses['min2']}}<br><br>
            </p>
            <img class="chibi-minus" :src="GetPathToImage(item.minuses['chibmin'])">
          </div>
          <p class="talent">Таланты</p>
          <div class="talents">
            <p class="talent-name">{{item.talent["talent-name1"]}}</p>
            <div class="talent-description-all">
              <div class="talent-description">
                Атака
                <div class="attack">
                  <br>
                  Обычная атака:<br><br>
                  {{item.attacks["standard-description"]}}<br><br>
                  <img :src="GetPathToImage(item.attacks['standard-presentation'])">
                </div>
                <div class="attack-hold">
                  Заряженная атака:<br><br>
                  {{item.attacks["hold-description"]}}
                  <br><br>
                  <img :src="GetPathToImage(item.attacks['hold-presentation'])">
                </div>
                <div class="attack-up">
                  Атака в падении:<br><br>
                  {{item.attacks["up-description"]}}
                  <br><br>
                  <img :src="GetPathToImage(item.attacks['up-presentation'])">
                </div>
              </div>
            </div>
            <p class="talent-name">{{item.talent["talent-name2"]}}</p>
            <div class="talent-description-all">
              <div class="talent-description">
                Элементальный навык
                <div class="attack">
                  <br>
                  {{item.attacks['en-description']}}<br><br>
                  {{item.attacks.enprop1}}<br>
                  {{item.attacks.enprop2}}<br>
                  {{item.attacks.enprop3s}}<br><br>
                  <img :src="GetPathToImage(item.attacks['en-presentation'])">
                </div>
                <div class="attack">
                  <br>
                  Долгое нажатие:<br><br>
                  {{item.attacks.end1}}<br><br>
                  {{item.attacks.end2}}<br><br>
                  <img :src="GetPathToImage(item.attacks['en-hold-presentation'])" alt="не существует">
                </div>
              </div>
            </div>
            <p class="talent-name">{{item.talent["talent-name3"]}}</p>
            <div class="talent-description-all">
              <div class="talent-description">
                Взрыв стихии
                <div class="attack">
                  <br>
                  {{item.attacks.ud1}}
                  <br><br>
                  {{item.attacks.ud2}}<br>
                  {{item.attacks.ud3}}<br>
                  {{item.attacks.uprop1}}<br>
                  {{item.attacks.uprop2}}
                  <br><br>
                  <div class="attack">
                    <img :src="GetPathToImage(item.attacks['ult-presentation'])">
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </details>
    </div>
  </main>
</template>

<script>
import mondshtat from "../data/mondshtat.json";
import liyue from "../data/liyue.json";
import inadzuma from "../data/inadzuma.json";
import character from "../data/character.json";

export default {
  name: "SquadView",
  data: function () {
    return {
      mondshtat: mondshtat,
      liyue: liyue,
      inadzuma: inadzuma,
      character: character,
      CharCase: false,
      charlist: [],
      charcaselist: [],
      XarXbox: false,
    }
  },
  methods: {
    Mama(el) {
      // console.log(el)
      if (el.innerText == "Подробнее") {
        el.innerText = "Скрыть"
        el.parentElement.parentElement.setAttribute('style', "margin-bottom: 400rem;")
      }
      else {
        el.innerText = "Подробнее"
        el.parentElement.parentElement.setAttribute('style', "margin-bottom: 0;")
      }
    },
    CalculatePercentage() {
      var charcaselist_temp = [];
      var character = this.character;
      var perc = document.querySelector(".purcent");
      this.charlist.forEach(function(i) {
        charcaselist_temp.push(character[i])
      })
      this.charcaselist = charcaselist_temp;
      var percent = 0;
      for (let key in this.charcaselist) {
        console.log(key)
        percent += this.charcaselist[key].puc
      };
      if (this.charlist.length === 4) {
        perc.innerHTML = String(percent) + "%";
        this.XarXbox = true;
      }
      else {
        alert("выберете 4 перонажей !")
      }
      // }
    },
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true
      } else {
        return false
      }
    },
    GetPathToImage: function (img) {
      return new URL(`../assets/${img}`, import.meta.url).href;
    },
    ShowCharCase() {
      this.CharCase = true
    },
    SetChar(el, charlist) {
      console.log(el)
      let a = document.getElementsByClassName("squad-container");

    for (let i in this.charlist) {
      if (el.getAttribute("id") == this.charlist[i]) {
        alert("такой персонаж уже есть!")
        return;
      }
    }
    if (this.charlist.length == 0) {
      a[0].replaceChild(el, a[0].children[0]);
      this.charlist.push(el.getAttribute("id"))
    }
    else if (this.charlist.length == 1) {
      a[0].replaceChild(el, a[0].children[1]);
      this.charlist.push(el.getAttribute("id"))
    }
    else if (this.charlist.length == 2) {
      a[0].replaceChild(el, a[0].children[2]);
      this.charlist.push(el.getAttribute("id"))
    }
    else if (this.charlist.length == 3) {
      a[0].replaceChild(el, a[0].children[3]);
      this.charlist.push(el.getAttribute("id"))
    }
    this.CharCase = false



      this.CharCase = false
    },
  }
}
</script>

<style scoped>

.mobile {
  text-align: center;
}

main{
  height: 56% !important;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  align-content: center;
}

.annotation {
  position: relative;
  right: 24%;
  font-size: 1vw;
  opacity: 0.4;
  width: max-content;
  margin-bottom: 5%;
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
.upper {
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
}

.squad-container {
  background: rgba(61, 28, 95, 0.6);
  border: 10px solid #5C2B8E;
  border-radius: 20px;
  width: 63vw;
  height: 15vw;
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: nowrap;
  margin-left: 2vw;
}

.squad-container .case {
  width: 27%;
}

.char-card-position {
  background: none;
  border: 6px solid #17042a;
  border-radius: 20px;
  height: 65%;
  width: 7vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 2rem;
}

.char-card-photo {
  height: 100%;
  width: auto;
}

.purcent {
  border: 15px solid #FFCF0D;
  border-radius: 300px;
  margin-left: 7.5vw;
  width: 15vw;
  height: 15vw;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #FFCF0D;
  font-size: 4vw;
}

.check {
  position: absolute;
  bottom: 1vh;
  right: 1vh;
  height: 18%;
  width: 2.5vw;
  background-color: #FFCF0D;
  color: black;
  border-radius: 300px;
  display: flex;
  font-size: 2vw;
  align-content: center;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.char-case {
  height: auto;
  width: 95.5vw;
  margin-top: 10vh;
  background: rgba(61, 28, 95, 0.6);
  border: 10px solid #5C2B8E;
  border-radius: 20px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: center;
}

.char-card {
  background: rgba(76, 194, 241, 0.4);
  border: 7px solid #4CC2F1;
  border-radius: 20px;
  height: 17.5vh;
  width: 7.3vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 4vh 4vw 0 4vw;
  cursor: pointer;
}

.char-card.elektro {
  background: rgba(167, 87, 203, 0.4);
  border: 7px solid #A757CB;
  border-radius: 20px;
  height: 17.5vh;
  width: 7.3vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 4vh 4vw 0 4vw;
}

.char-card.piro {
  background: rgba(254, 146, 93, 0.4);
  border: 7px solid #FE925D;
  border-radius: 20px;
  height: 17.5vh;
  width: 7.3vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 4vh 4vw 0 4vw;
}

.char-card.anemo {
  background: rgba(87, 252, 188, 0.4);
  border: 7px solid #57FCBC;
  border-radius: 20px;
  height: 17.5vh;
  width: 7.3vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 4vh 4vw 0 4vw;
}

.char-card.geo {
  background: rgba(253, 200, 39, 0.4);
  border: 7px solid #CC6E16;
  border-radius: 20px;
  height: 17.5vh;
  width: 7.3vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 4vh 4vw 0 4vw;
}

.char-card.crio {
  background: rgba(160, 237, 254, 0.4);
  border: 7px solid #58B3F5;
  border-radius: 20px;
  height: 17.5vh;
  width: 7.3vw;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 4vh 4vw 0 4vw;
}

.char-photo-card {
  height: 100%;
  width: auto;
}

.case {
  height: max-content;
  width: max-content;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  align-content: center;
}

p {
  margin: 1vh 0 5vh 0;
  font-size: 1.2rem;
  text-align: center;
}

.char-card:hover {
  background: rgba(255, 204, 0, 0.4);
  border: 7px solid #FFCC00;
  transition: all 0.5s;
}

.plus {
  background: #17042a;
  border-radius: 300px;
  width: 40%;
  height: 30%;
  display: flex;
  font-size: 2rem;
  color: #31114b;
  align-content: center;
  justify-content: center;
  align-items: center;
  flex-wrap: nowrap;
  flex-direction: row;
  font-family: "TT_Skip-E";
  cursor: pointer;
}

.plus:hover {
  background: #FFCC00;
  color: #17042a;
  transition: all 0.5s
}

.xar-box {
  height: max-content;
  width: 96%;
  margin-top: 10vh;
  background: linear-gradient(102.81deg, rgba(61, 28, 95, 0.6) 51.78%, rgba(76, 194, 241, 0.6) 91.5%);
  border: 10px solid #5C2B8E;
  border-radius: 20px;
  display: flex;
  /* overflow: hidden; */
  flex-direction: row;
  flex-wrap: wrap;
  align-content: center;
  justify-content: flex-end;
}

.char-box {
  height: 75vh;
  width: auto;
  position: relative;
  left: 5vw;
}


.informasa {
  left: 5vw;
  position: absolute;
  width: 40%;
  height: auto;
}

.xar-name {
  font-size: 5rem;
}

.xar-ratting {
  display: flex;
  border: 10px solid #ffbf7f;
  color: #ffbf7f;
  height: 35vh;
  width: 18vw;
  border-radius: 30px;
  align-items: center;
  justify-content: center;
  align-content: center;
  flex-wrap: nowrap;
  flex-direction: row;
  font-size: 9rem;
  cursor: pointer;
}

.xar-ratting:hover {
  background: #ffbf7f;
  border: none;
  color: black;
  transition: all 0.5s;
}

.xar-weapon {
  margin-top: 2vw;
}


details summary {
  background: #FFCF0D;
  border-radius: 20px;
  font-family: "TT_Skip-E";
  position: relative;
  left: 7%;
  bottom: 7%;
  margin-top: 1.5%;
  height: 5vw;
  top: -15vh;
  border: 0;
  font-size: 1.4vw;
  width: 14vw;
  cursor: pointer;
  color: #341C00;
  display: flex;
  justify-content: center;
  align-items: center;
  outline: none;
}


details summary::-webkit-details-marker {
  display: none;
}

details .isesc {
  padding: 10%;
  position: absolute;
  top: 1vh;
  border-radius: 2vw;
  width: 100%;
  font-size: 2rem;
  background: radial-gradient(50% 50% at 50% 50%, rgba(30, 0, 61, 0.9) 0%, rgba(0, 0, 0, 0.9) 100%);
}

details {
  width: 100%;
  position: relative;
  left: 0;
  height: 0;
  bottom: 0%;
}

.pluses {
  font-size: 2rem;
}

.minuses {
  font-size: 2rem;
}

.plusess {
  font-size: 1.4rem;
  position: relative;
  width: 45vw;
  text-align: left;
}

.minusess {
  font-size: 1.4rem;
  position: relative;
  width: 45vw;
  text-align: left;
}

.plus-minus {
  display: flex;
  align-items: center;
}

.chibi-plus {
  width: 15vw;
  left: 5%;
  bottom: 5%;
}

.chibi-minus {
  width: 15vw;
  left: 5%;
  bottom: 5%;
}

.talent {
  font-size: 3rem;
}

.talent-name {
  font-size: 2rem;
  position: relative;
  width: 45vw;
  text-align: left;
  margin-top: 10vh;
}

.talent-description {
  font-size: 1.4rem;
  position: relative;
  width: 45vw;
  text-align: left;
}


.talent-gif {
  width: 35vw;
  margin: 2vh 0 2vh 0;
}

.xar-box.piro {
  background: linear-gradient(102.81deg, rgba(61, 28, 95, 0.6) 51.78%, rgba(254, 146, 93, 0.6) 91.5%);
}

.xar-box.elektro {
  background: linear-gradient(102.81deg, rgba(61, 28, 95, 0.6) 51.78%, rgba(193, 89, 240, 0.6) 91.5%);
}

.xar-ratting.a {
  border-color: #ffff7f;
  color: #ffff7f;
}

.xar-ratting.a:hover {
  background-color: #ffff7f;
  color: black;
}

.xar-ratting.b {
  border-color: #bfff7f;
  color: #bfff7f;
}

.xar-ratting.b:hover {
  background-color: #bfff7f;
  color: black;
}
</style>