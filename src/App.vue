<template>
  <top-section  :playTime="playTime"></top-section>
  <game-field
    :gameArray="gameArray"
    @choose-item="getChoosedItem"
    v-if="youPicked === null"
    :isBattle="isBattle"
  ></game-field>
  <battle-screen
    v-if="youPicked !== null"
    :pickedItem="youPicked"
    :theHouseItem="theHousePicked"
    :isBattle="isBattle"
    @playAgain="playAgain"
    :gameResult="gameResult"
  ></battle-screen>
  <section class="rules">
    <button @click="showRules" class="rules-btn">RULES</button>
    <rules-dialog
      v-if="isShowRules"
      :isRules="isShowRules"
      @close="closeDialog"
    ></rules-dialog>
  </section>
</template>

<script>
import RulesDialog from "./components/RulesDialog.vue";
import TopSection from "./components/TopSection.vue";
import GameField from "./components/GameField.vue";
import BattleScreen from "./components/BattleScreen.vue";

export default {
  name: "App",
  components: {
    RulesDialog,
    TopSection,
    GameField,
    BattleScreen,
  },
  data() {
    return {
      gameArray: ["paper", "scissors", "rock"],
      isShowRules: false,
      youPicked: null,
      theHousePicked: null,
      isBattle: false,
      gameResult: '',
      playTime: 0
    };
  },
  methods: {
    showRules() {
      this.isShowRules = true;
    },
    closeDialog() {
      this.isShowRules = false;
    },
    getChoosedItem(item) {
      this.isBattle = true;
      this.youPicked = item.youPicked;
      this.theHousePicked = item.randomPicked;
      this.gameResult = item.gameResult;
      this.playTime ++;
    },
    playAgain(){
      this.isBattle= false;
      this.youPicked = null;
    }
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@400;500;600;700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-family: "Barlow Semi Condensed", sans-serif;
}
#app {
  background: linear-gradient(
    182deg,
    rgba(31, 55, 86, 1) 0%,
    rgba(20, 21, 57, 1) 100%
  );
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
}
.rules-btn {
  border: none;
  background: none;
  color: white;
  border: 1px solid white;
  padding: 1rem 2rem;
  border-radius: 1rem;
}
.rules {
  width: 100%;
  text-align: end;
  padding-right: 5rem;
}
</style>
