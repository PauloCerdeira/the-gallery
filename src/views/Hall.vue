<template>
  <div class="hall-container">
    <div @click="move(-1)" class="left-move">
      <i class="fas fa-arrow-left"></i>
    </div>
    <div class="exhibit-container">
      <div class="row">
        <div class="col-6">
          <img
            class="thumbnail"
            src="http://beepeers.com/assets/images/commerces/default-image.jpg"
            alt=""
          />
        </div>
        <div class="col-6 ">
          <div class="info-container" >
            <div class="col-12 mb-3 d-flex justify-content-between">
              <div class="col-9">
                <h1>{{ selectedExhibit.title }}</h1>
              </div>

              <div class="col">
                <h1><i :class="selectedExhibit.icon"></i></h1>
              </div>
              <h1></h1>
            </div>
            <div class="col-12">
              <h4>
                {{ selectedExhibit.description }}
              </h4>
            </div>
            <div class="col-12 exhibit-button-container">
              <button class="exhibit-button">Visitar!</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div @click="move(1)" class="right-move">
      <i class="fas fa-arrow-right"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      index: 0,
      selectedExhibit: {
        title: "",
        description: "",
        imagePath: "",
        icon: "",
        exhibitPath: "/",
      },
      exhibits: [
        {
          title: "Calculadora",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur, obcaecati aliquid officia atque vitae autem e id corporis. Cum maxime veritatis quae quo accusantium nobis architecto consequatur aperiam impedit.",
          backgroundColor: "#3e753eb8",
          highlightColor: '#f7aec1',
          imagePath: "calculadora",
          icon: "fas fa-calculator",
          exhibitPath: "/calculadora",
        },
        {
          title: "Restaurante",
          description:
            "Lorem ipsum dolor sit  adipisicing elit. Aspernatur, obcaecati aliquid officia atque vitae autem perspiciatis eaque id corporis. Cum maxime veritatis quae quo accusantium nobis architecto consequatur aperiam impedit.",
          backgroundColor: "#821717bf",
          highlightColor: '#70c3ed',
          imagePath: "restaurante",
          icon: "fas fa-utensils",
          exhibitPath: "/restaurante",
        },
        {
          title: "Nubank",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum maxime veritatis quae quo accusantium nobis architecto consequatur aperiam impedit.",
          backgroundColor: "#0b0b92b8",
          highlightColor: '#fdb64e',
          imagePath: "nubank",
          icon: "fas fa-money-check",
          exhibitPath: "/nubank",
        },
      ],
    };
  },
  async created() {
    let isso = this;
    setTimeout(function() {
      isso.selectedExhibit = isso.exhibits[0];
      isso.move(0);
    }, 1000);
  },
  methods: {
    move(number) {
      this.index += number;
      this.index < 0 ? (this.index = this.exhibits.length - 1) : null;
      this.index > this.exhibits.length - 1 ? (this.index = 0) : null;
      this.selectedExhibit = this.exhibits[this.index];

      document.documentElement.style
    .setProperty('--main-color', this.selectedExhibit.highlightColor);
    document.documentElement.style
    .setProperty('--background-color', this.selectedExhibit.backgroundColor);
    },
  },
};
</script>

<style scoped>
.hall-container {
  transition: background ease-in 0.7s;
  align-items: center;
  align-content: center;
  display: flex;
  height: 100%;
  width: 100%;
  background: var(--background-color);
  color: white;
}
.left-move,
.right-move {
  cursor: pointer;
  transition: transform ease-out 0.2s;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 15%;
  background: rgba(0, 0, 0, 0.247);
  color: white;
  font-size: 50px;
  box-shadow: rgb(0 0 0 / 24%) 1px -1px 12px 20px;
}
.left-move:hover {
  transform: translateX(20px);
}
.right-move:hover {
  transform: translateX(-20px);
}
.left-move > *,
.right-move > * {
  transition: transform ease-out 0.2s, color 0.1s;
}
.left-move:hover > *,
.right-move:hover > * {
  transform: scale(1.5);
}
.left-move:active > *,
.right-move:active > * {
  transform: scale(1.2);
  color: grey;
}
.exhibit-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50%;
  margin: 0px 10%;
  height: 100%;
}
.thumbnail {
  box-shadow: rgb(0 0 0 / 24%) 15px 16px 16px 7px;
  border-radius: 25px;
  width: 90%;
  margin: 5%;
}
.info-container {
  text-align: left;
  position: relative;
  margin: 5%;
  height: 90%;
}
.exhibit-button {
  transition: all 0.2s;
  position: relative;
  color: white;
  background: none;
  border-radius: 25px;
  padding: 8px 5px;
  margin: 5px 0px;
  width: 100%;
  font-weight: bold;
  font-size: 20px;
  border: 2px solid white;
}
.exhibit-button:hover {
  color: var(--main-color);
  border: 2px solid var(--main-color);
  box-shadow: inset var(--main-color) 0px 0px 13px 5px;
}
.exhibit-button:hover.exhibit-button:after {
  top: -4px;
  border-radius: 25px;
  box-shadow: var(--main-color) 0px 0px 17px 6px;
  content: "";
  left: 0px;
  position: absolute;
  padding: 10px 5px;
  margin: 5px 0px;
  width: 100%;
  border: 2px solid var(--main-color);
  height: 43px;
}
.exhibit-button:hover.exhibit-button:before {
    border-radius: 25px;
    box-shadow:var(--main-color) 0px 0px 17px 6px;
    opacity: 0.3;
    content: "";
    left: 0px;
    position: absolute;
    top: 50%;
    width: 100%;
}
.exhibit-button:active.exhibit-button:before {
  box-shadow: white 0px 0px 17px 6px;
}
.exhibit-button:active.exhibit-button:after {
  border: 2px solid white;
  box-shadow: white 0px 0px 17px 6px;
}
.exhibit-button:active {
  color: white;
  border: 2px solid white;
  box-shadow: inset white 0px 0px 13px 5px;
}

.exhibit-button-container {
  position: absolute;
  bottom: 0px;
}
</style>
