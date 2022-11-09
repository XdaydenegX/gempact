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
    <div class="weapons-categories-container">
      <div class="weapons-categories">
        <div class="weapons-category" v-for="category in weapons_categories" v-bind="{id: category.id}" v-on:click="setCategory($event.target)">
          <div class="weapon-category-photo">
            <img :src="GetPathToImage(category.bg)">
          </div>
          <h1>{{category.name}}</h1>
        </div>
      </div>
    </div>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
  <WeaponsDetail :weapons="this.weapons_sword"  v-bind:is_show="sword"></WeaponsDetail>
    <WeaponsDetail :weapons="this.weapons_two_hand_sword" v-bind:is_show="two_hand_sword"></WeaponsDetail>
<WeaponsDetail :weapons="this.weapons_spear" v-bind:is_show="spear"></WeaponsDetail>
 <WeaponsDetail :weapons="this.weapons_bow" v-bind:is_show="bow"></WeaponsDetail>
<WeaponsDetail :weapons="this.weapons_catalyst" v-bind:is_show="catalyst"></WeaponsDetail>
  </main>
</template>

<script>
import weapons_categories from '../data/weapons_categories.json'
import weapons_sword from '../data/weapons_sword.json'
import weapons_two_hand_sword from '../data/weapons_two_hand_sword.json'
import weapons_spear from '../data/weapons_spear.json'
import weapons_bow from '../data/weapons_bow.json'
import weapons_catalyst from '../data/weapons_catalyst.json'
import WeaponsDetail from "../components/WeaponsDetail.vue";
export default {
  components: {
    WeaponsDetail
  },
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
    ChoiseCategory(category) {
      if (weapons_categories.id == category) {
        if (`weapons_${category}`.category == category) {
          let weapon_temp = `weapons_${category}`;
          weapon_temp.forEach(function (i) {
            this.weapon = weapon_temp[i];
          })
        }
      }
    },
    GetCategory(category) {
      switch (category) {
        case "sword":
          return this.sword;
        case "two-hand-sword":
          return this.two_hand_sword;
        case "spear":
          return this.spear;
        case "bow":
          return this.bow;
        case "catalyst":
          return this.catalyst;
      }
    },
    setCategory(el) {
      var id = el.parentElement.parentElement.id;
      switch (id) {
        case "sword":
          this.sword = !this.sword;
          break;
        case "two-hand-sword":
          this.two_hand_sword = !this.two_hand_sword;
          break;
        case "spear":
          this.spear = !this.spear;
          break;
        case "bow":
          this.bow = !this.bow;
          break;
        case "catalyst":
          this.catalyst = !this.catalyst;
          break;
      }
      el.parentElement.parentElement.classList.toggle('active');
    }
  },
  name: "WeaponView",
  data: function () {
    return {
      bow: false,
      catalyst: false,
      spear: false,
      sword: false,
      two_hand_sword: false,
      weapons_categories: weapons_categories,
      weapons_sword: weapons_sword,
      weapons_two_hand_sword: weapons_two_hand_sword,
      weapons_spear: weapons_spear,
      weapons_bow: weapons_bow,
      weapons_catalyst: weapons_catalyst,
      // isReturnButton,
    }
  }
}
</script>

<style>

.annotation {
  position: relative;
  left: 1%;
  font-size: 1vw;
  opacity: 0.4;
  width: max-content;
  margin-bottom: 10%;
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

.weapons-category {
  width: 20vw;
  display: flex;
  height: 40vh;
  background: #390A68;
  border: 0.5rem solid #27004E;
  border-radius: 1rem;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
  margin: 2rem;
}

.weapon-category-photo {
  width: 18em;
  height: 18em;
  overflow: hidden;
  background: #FFCC00;
  border: 0.25rem solid #100020;
  border-radius: 100rem;
}

.weapons-categories {
  width: 82vw;
  justify-content: space-evenly;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: flex-start;
  align-items: center;
}


.weapons-categories-container {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
}

.weapon-list {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
  margin: 0 0 2% 0;
}



.weapon-photo.epic {
  background: radial-gradient(96.08% 96.08% at 50% 50%, #D3A8FF 0%, #390A68 100%);
  border: 0.3rem solid #27004E;
  border-radius: 1rem;
  width: 10vw;
  display: flex;
  height: 20vh;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
}
.weapon-photo.legendary {
  background: radial-gradient(96.08% 96.08% at 50% 50%, #FFCC00 0%, #390A68 100%);
  border: 0.3rem solid #27004E;
  border-radius: 1rem;
  width: 10vw;
  display: flex;
  height: 20vh;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
}

.weapon-info {
  background: #390A68;
  border: 0.3rem solid #27004E;
  border-radius: 1rem;
  width: 50vw;
  height: 20vh;
  font-size: large;
  padding: 1%;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;

}

.weapon-photo img {
  object-fit: cover;
  width: 100%;
  height: 100%;
}

.weapon-info h2 {
  color: #FFCC00;
}

.weapons-category.active {
  border: 0.5rem solid #FFCC00;
}

</style>