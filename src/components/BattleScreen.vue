<template>
  <section class="game-field">
    <div class="you-picked">
      <h3>YOU PICKED</h3>
      <div class="container">
        <base-item
          class="you-pick-circle"
          :id="pickedItem.id"
          :color="pickedItem.color"
          :src="pickedItem.src"
          :isBattle="isBattle"
        ></base-item>
      </div>
    </div>
    <div class="middle" :class="showResult ? 'show' : 'hide'">
      <h2>{{ gameResult }}</h2>
      <button @click="playAgain">PLAY AGAIN</button>
    </div>
    <div class="the-house-picked">
      <h3>THE HOUSE PICKED</h3>
      <div class="container">
        <div class="shadow" v-if="!showRandomPick"></div>
        <base-item
          v-if="showRandomPick"
          :id="theHouseItem.id"
          :color="theHouseItem.color"
          :src="theHouseItem.src"
          :isBattle="isBattle"
        ></base-item>
      </div>
    </div>
  </section>
</template>
<script>
import BaseItem from "./BaseItem.vue";
export default {
  components: { BaseItem },
  props: ["pickedItem", "theHouseItem", "isBattle", "gameResult"],
  data() {
    return {
      showRandomPick: false,
      showResult: false,
      id:''
    };
  },
  mounted() {
    this.id= setTimeout(() => {
      this.showRandomPick = true;
    }, 1000);
  },
  watch: {
    showRandomPick: function () {
      setTimeout(() => {
        this.showResult = true;
      }, 1000);
    },
  },
  methods:{
    playAgain(){
        clearTimeout(this.id);
        this.$emit('playAgain');
    }
  }
};
</script>

<style scoped>
.middle.show {
  display: flex;
}
.middle.hide {
  display: none;
}
.shadow {
  width: 12rem;
  height: 12rem;
  border-radius: 999px;
  background-color: rgba(0, 0, 0, 0.1);
}
h3 {
  height: 20%;
  z-index: 100;
}
.game-field {
  display: flex;
  position: relative;
  width: 80%;
  height: 50%;
  align-items: center;
  justify-content: center;
  display: flex;
  justify-content: space-around;
  color: white;
}
.container {
  width: 20rem;
  height: 20rem;
}
.container,
.you-picked,
.the-house-picked,
.middle {
  display: flex;
  align-items: center;
  justify-content: center;
}
.you-pick-circle{
    box-shadow: 0 0 0 2em rgba(0,0,0,0.1),
              0 0 0 4em  rgba(0,0,0,0.1),
              0 0 0 6em  rgba(0,0,0,0.1);
  margin: 2em;
  padding:2em;
  border-radius: 999px;
}
.you-picked,
.the-house-picked {
  height: 50%;
  flex-direction: column;
  font-size: 2rem;
  /* background-color: #dcdcdc; */
  justify-content: space-between;
}
.middle {
  flex-direction: column;
  justify-content: space-around;
  height: 50%;
}
.middle h2 {
  font-size: 3rem;
}
.middle button {
  border: none;
}

.middle button {
  box-shadow: inset 0px 1px 0px 0px #ffffff;
  background: linear-gradient(to bottom, #ffffff 5%, #f6f6f6 100%);
  background-color: #ffffff;
  border-radius: 6px;
  border: 1px solid #dcdcdc;
  display: inline-block;
  cursor: pointer;
  color: #3a3a3a;
  font-family: Arial;
  font-size: 15px;
  font-weight: bold;
  padding: 6px 24px;
  text-decoration: none;
  text-shadow: 0px 1px 0px #ffffff;
}
.middle buttonn:hover {
  background: linear-gradient(to bottom, #f6f6f6 5%, #ffffff 100%);
  background-color: #f6f6f6;
  color: rgb(196, 5, 5);
}
.middle button:active {
  position: relative;
  top: 1px;
}
</style>
