<template>
  <section class="game-field">
    <div
      v-for="item in gameArray"
      :key="item"
      class="container"
      :class="getColor(item)"
    >
      <base-item
        :id="item"
        :color="getColor(item)"
        :src="getImgUrl(item)"
        @click="chooseOne(item)"
        :isBattle="isBattle"
      ></base-item>
    </div>
    <img
      class="triangle"
      src="../assets/images/bg-triangle.svg"
      alt="triangle"
    />
  </section>
</template>
<script>
import BaseItem from "./BaseItem.vue";

export default {
  components: { BaseItem },
  props: ["gameArray", "isBattle"],
  data() {
    return {
      choosedItem: {
        id: "",
        color: "",
        src: "",
      },
      randomItem:{
        id: "",
        color: "",
        src: "",
      },
      gameResult:''
    };
  },
  methods: {
    getColor(item) {
      if (item === "paper") {
        return "blue";
      } else if (item === "rock") {
        return "red";
      } else if (item === "scissors") {
        return "yellow";
      }
    },
    getImgUrl(item) {
      return require("../assets/images/icon-" + item + ".svg");
    },
    chooseOne(item) {
      this.choosedItem = {
        id: item,
        color: this.getColor(item),
        src: this.getImgUrl(item)
      };
      this.getRandomItem();
      this.watchGameResult();
      this.$emit('choose-item', {youPicked: this.choosedItem, randomPicked: this.randomItem, gameResult:this.gameResult});
    },
    getRandomItemName(arr){
      const randomIndex = Math.floor(Math.random() * arr.length);
      const item = arr[randomIndex];
      return item;
    },
    getRandomItem(){
      const randomOne = this.getRandomItemName(this.gameArray);
      this.randomItem = {
        id: randomOne,
        color: this.getColor(randomOne),
        src: this.getImgUrl(randomOne)
      }
    },
    watchGameResult(){
        const pickedItemName =this.choosedItem.id;
        const randomItemName = this.randomItem.id;
        if(pickedItemName === randomItemName){
            this.gameResult ="IT'S A TIE"
        }
        if(pickedItemName === 'paper' && randomItemName === 'rock' ||
        pickedItemName === 'rock' && randomItemName === 'scissors' ||
        pickedItemName === 'scissors' && randomItemName === 'paper'
        ){
            this.gameResult ="YOU WIN!"
        }if(pickedItemName === 'rock' && randomItemName === 'paper' ||
        pickedItemName === 'scissors' && randomItemName === 'rock' ||
        pickedItemName === 'paper' && randomItemName === 'scissors'){
            this.gameResult ="YOU LOSE!"
        }
        
    }
   
  },
};
</script>

<style scoped>
.game-field {
  display: flex;
  position: relative;
  width: 50%;
  height: 50%;
  align-items: center;
  justify-content: center;
}
.triangle {
  width: 50%;
  height: 100%;
  z-index: 1;
}

.container {
  position: absolute;
  z-index: 10;
}
.blue {
  top: -10%;
  right: 15%;
}
.red {
  bottom: 0%;
}
.yellow {
  top: -10%;
  left: 15%;
}
</style>
