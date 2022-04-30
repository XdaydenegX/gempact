<template>
  <main>
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
    }
  },
  methods: {
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
        percent += this.charcaselist[key].puc
      };
      if (this.charlist.length === 4) {
        perc.innerHTML = String(percent) + "%";

      }
      else {
        alert("выберете 4 перонажей !")
      }
      // }
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
  width: 50vw;
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
  width: 20%;
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
</style>