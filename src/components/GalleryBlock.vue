<template>
  <div class="card-mobile" v-if="isMobile()" v-for="item in cards" v-bind="{id: item.id}">
    <h1 class="card-name-mobile">{{item.title}}</h1>
    <div class="container-mobile">
      <img :src="GetPathToImage(item.mobile)">
      <div class="needflex">
        <details>
          <summary>〉</summary>
          <div class="info-mobile">
            <h1 class="title-info-mobile">{{item.titleCard}}</h1>
            <p class="description-mobile">{{item.text}}</p>
            <button class="go" @click="goURL(item.to_url)">Перейти</button>
            <span class="ant-info">{{item.description}}</span>
          </div>
        </details>
      </div>
    </div>
  </div>


  <div v-else class="card" v-for="item in cards" v-bind="{id: item.id}">
    <h1 class="card-title">{{item.title}}</h1>
    <div class="container" v-bind:class="{right: item.right}">
    <div class="container-img" v-bind:class="[item.img]"></div>
      <h1>{{item.titleCard}}</h1>
      <p>{{item.text}}</p>
      <button @click="goURL(item.to_url)">Перейти</button>
      <span>{{item.description}}</span>
    </div>
  </div>

</template>



<script>
export default {
  name: "GalleryBlock",
  data: function() {
    return {
      cards: [ { id: "card-1",  title: "Галерея персонажей", img: "gallery", titleCard: "Демонстрация  персонажей игры и краткое описание", text: "Формирование представлений игрока об\n" +
            "определенном персонаже, демонстрация\n" +
            "артов и видеоматериалов, а так же\n" +
            "короткое описание его личной истории.", description: "Будут преставлены только персонажи\n" +
            "из тех регионов, которые уже добавлены\n" +
            "в игру. (Мондштадт, Ли Юэ, Инадзума)", to_url: '/gallery', mobile: "mobile/gallery-bg.png"},
        { id: "card-2", title: "Подбор отрядов", img: "squad", right: true, titleCard: "Подбор персонажей в отряды в помощь новичкам", text: "Иногда  у новых игроков, получивших своих первых персонажей из баннеров могут\n" +
              "возникнуть проблемы с составленем отрядов.\n" +
              "В данном разделе будет возможность собрать отряд из 4 персонажей, а так же просмотреть\n" +
              "их способности и возможные элементальные реакции между персонажами отрядами. ", description: "Так же будут представлены только персонажи из\n" +
              "уже вышедших регионов. ", to_url: '/squad', mobile: "mobile/squad-bg.png"},
        {id: "card-3",title: "Оружие", img: "weapon", titleCard: "Перебор вариантов вооружения для ваших персонажей", text: "Выбор лучших вариантов оружия для ваших персонажей. Вы сможите просмотреть\n" +
              "достаточно возможных вариаций, подобрать \n" +
              "оружие различных рангов (легендарное, \n" +
              "эпическое и др) а так же материалы, требуемые\n" +
              "для его максимальной прокачки.", description: "Оружие и персонажи по-прежнему будут\n" +
              "только те, что есть в игре на данный момент", to_url: '/weapon', mobile: "mobile/weapon-bg.png"}],
      infoVisible: false
    }
  },
  methods: {
    goURL: function(url) {
      if (url) {
        window.location = url;
      }
    },
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true
      } else {
        return false
      }
    },
    openInfo(el) {
      console.log(el)
    },
    GetPathToImage: function (img) {
      return new URL(`../assets/${img}`, import.meta.url).href;
    }
  }
}
</script>
<style scoped>

.card-mobile {
  width: 100%;
  height: max-content;
  margin: 0vw 0 10vw 0;
  padding-top: 21.8vh;
}

.card-name-mobile {
  font-size: 1.5rem;
  text-align: center;
}

.container-mobile {
  width: 100%;
  height: 100%;
}

img {
  object-fit: cover;
  width: 100%;
}

details {
  display: flex;
  justify-content: center;
  transition: all 0.9s ease-in-out;
  margin-bottom: 0vh;
}

details[open] {
  transition: all 0.9s ease-in-out;
  margin-bottom: 5vh;

}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes slide {
  0%    { opacity: 0; transform:  translate(0, -10px); }
  100%  { opacity: 1; transform:  translate(0, 0); }
}

summary {
  position: absolute;
  width: 100px;
  top: -15vh;
  right: 8vw;
  margin: 0;
}

details > summary {
  width: 120px;
  height: 120px;
  background-color: #FFCF0D;
  border-radius: 50%;
  list-style: none;
  border: none;
  text-align: center;
  display: flex;
  border: none;
  font-size: -webkit-xxx-large;
  justify-content: center;
  align-items: center;
  font-family: "TT_Skip-E";
  color: #341C00;
  transform: rotate(90deg);
  transition: all 0.5s;

}

details[open] summary {
  transform: rotate(270deg);
  transition: all 0.5s;
}

details .info-mobile {
  transition: all 0.5s ease-in-out;
  transform: translateY(-10px);
  opacity: 0;
}

details[open] .info-mobile {
  transform: translateY(0px);
  opacity: 1;
  transition: all 0.5s ease-in-out;
}

.title-info-mobile {
  position: relative;
  text-align: center;
  font-size: 5.5vw;
}

p {
  display: flex;
  text-align: center;
  margin-top: 2vw;
}

.go {
  height: 15vw;
  width: 45vw;
  margin: 2.5vw;
  background: #FFCF0D;
  color: #341C00;
  border: none;
  border-radius: 3vw;
  font-size: 6vw;
  font-family: "TT_Skip-E";
}

span {
  text-align: center;
  font-size: 3vw;
  opacity: 0.5;
}

.info-mobile {
  display: flex;
  margin-top: 20%;
  width: 100vw;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.needflex {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-end;
  align-content: center;
  flex-wrap: nowrap;
}






.card-title {
  left: 8%;
  width: max-content;
  color: white;
  font-style: normal;
  font-weight: 400;
  font-size: xxx-large;
}
.container {
  width: 90%;
  height: 35.6vw;
  left: 5%;
  display: flex;
  margin: 5%;
  background: rgba(61, 28, 95, 0.6);
  border: 10px solid #5C2B8E;
  border-radius: 60px;
  margin: 0;
  padding: 0;
  background-position: center center;
  background-size: cover;
  background-image: url("../assets/bg-container.png");
  overflow: hidden;
}
.container-img {
  width: auto;
  height: auto;
  position: absolute;
  background-position-y: center;
  background-size: cover;
  width: 46%;
  height: 100%;
}
.container-img.gallery {
  background-image: url("../assets/gallery-img.png");
}

.container-img.squad {
  background-image: url("../assets/squad-img.png");

}
.container-img.weapon {
  background-image: url("../assets/weapon-img.png");
}
.container h1 {
  color: white;
  font-size: 2.5vw;
  text-align: center;
  /* left: 0; */
   position: absolute;
  width: 52%;
  right: 6%;
  display: flex;
  top: 2%;
  /* left: calc(50% - 52% /2); */
  justify-content: center;
  line-height: 4vw;
}
.container.right h1 {
  left: 5%;
}
.container p {
  font-size: 1.5vw;
  text-align: center;
  line-height: normal;
  position: absolute;
  width: 40%;
  right: 12%;
  top: 28%;
  margin-top: 0;
}
.container.right p {
  left: 8%;
  width: 46%;
}
.container button {
  background: #FFCF0D;
  border-radius: 1vw;
  font-family: "TT_Skip-E";
  position: absolute;
  right: 24%;
  height: 5.5vw;
  border: 0;
  font-size: 2vw;
  bottom: 6vw;
  width: 14vw;
  cursor: pointer;
  color: #341C00;
}
.container.right button {
  left: 23.5%;
  bottom: 14%;
  color: #341C00
}

.container span {
  position: absolute;
  width: 22vw;
  bottom: 2%;
  opacity: 0.6;
  right: 19.2%;
  /* left: 5%; */
  /* word-break: break-word; */
  text-align: center;
  font-size: 0.8vw;

}

.container.right span {
  left: 18.9%;
}

.card {
margin-top: 5%;
margin-bottom: 5%;
position: relative;
}
.right {
justify-content: flex-end;
}

</style>