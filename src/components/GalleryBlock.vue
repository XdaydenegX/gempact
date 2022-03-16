<template>
  <div class="card" v-for="item in cards"  v-bind="{id: item.id}">
    <h1 class="card-title">{{item.title}}</h1>
    <div class="container" v-bind:class="{right: item.right}">
    <div class="container-img" v-bind:class="[item.img]"></div>
      <h1>{{item.titleCard}}</h1>
      <p>{{item.text}}</p>
      <button>Перейти</button>
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
            "в игру. (Мондштадт, Ли Юэ, Инадзума)"},
        { id: "card-2", title: "Подбор отрядов", img: "squad", right: true, titleCard: "Подбор персонажей в отряды в помощь новичкам", text: "Иногда  у новых игроков, получивших своих первых персонажей из баннеров могут\n" +
              "возникнуть проблемы с составленем отрядов.\n" +
              "В данном разделе будет возможность собрать отряд из 4 персонажей, а так же просмотреть\n" +
              "их способности и возможные элементальные реакции между персонажами отряда. ", description: "Так же будут представлены только персонажи из\n" +
              "уже вышедших регионов. "},
        {id: "card-3",title: "Оружие", img: "weapon", titleCard: "Перебор вариантов вооружения для ваших персонажей", text: "Выбор лучших вариантов оружия для ваших персонажей. Вы сможите просмотреть\n" +
              "достаточно возможных вариаций, подобрать \n" +
              "оружие различных рангов (легендарное, \n" +
              "эпическое и др) а так же материалы, требуемые\n" +
              "для его максимальной прокачки.", description: "Оружие и персонажи по-прежнему будут\n" +
              "только те, что есть в игре на данный момент"}]
    }
  },
  methods: {
    getpath: function(path) {
      return require(path);
    }
  }

}
</script>
<style scoped>
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
}
.container-img {
  border-radius: 50px;
  width: auto;
  height: auto;
  position: absolute;
  background-position-y: center;
  background-size: cover;
  width: 43%;
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
  font-size: xxx-large;
  text-align: center;
  /* left: 0; */
   position: absolute;
  width: 52%;
  right: 6%;
  display: flex;
  top: 2%;
  /* left: calc(50% - 52% /2); */
  justify-content: center;
}
.container.right h1 {
  left: 6%;
}
.container p {
  font-size: x-large;
  text-align: center;
  position: absolute;
  width: 53%;
  right: 6%;
  top: 30%;
}
.container.right p {
  left: 8%;
  width: 50%;
}
.container button {
  background: #FFCF0D;
  border-radius: 20px;
  font-family: "TT_Skip-E";
  position: absolute;
  right: 24%;
  height: 103px;
  border: 0;
  font-size: xx-large;
  bottom: 26%;
  width: 15%;
}
.container.right button {
  left: 24%;
  bottom: 23%;
}

.container span {
  position: absolute;
  width: 22%;
  bottom: 2%;
  opacity: 0.6;
  right: 21%;
  /* left: 5%; */
  /* word-break: break-word; */
  text-align: center;

}

.container.right span {
  left: 20%;
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