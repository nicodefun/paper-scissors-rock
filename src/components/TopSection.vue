<template>
  <section class="top-section">
    <div class="text-area">
      <p>ROCK</p>
      <p>PAPER</p>
      <p>SCISSORS</p>
    </div>
    <div class="score-container">
      <p class="score-container__text">SCORE</p>
      <p class="score-container__number">{{playTime}}</p>
    </div>
  </section>
</template>
<script>
export default {
  props:["playTime"]
};
</script>
<style scoped>
.top-section {
  width: 50%;
  border: 0.2rem solid rgb(212, 212, 212, 0.3);
  border-radius: 1rem;
  display: flex;
  height: 15%;
  overflow-y: hidden;
  justify-content: space-between;
  align-items: center;
}
.text-area {
  font-size: 1.7rem;
  font-weight: 700;
  color: white;
  padding: 0.5rem 1.5rem;
}
.score-container{
  width: 8rem;
  height: 80%;
  border-radius: 1rem;
  margin-right: 1.5rem;
  background-color: white;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.score-container__number{
  font-size: 3rem;
  font-weight: 700;
  color: rgb(89, 89, 89);
}
.score-container__text{
  font-size: 0.9rem;
  font-weight: 700;
  color: rgb(160, 168, 168);
}

</style>
