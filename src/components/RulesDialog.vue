<template>
  <div class="modal" @click="$emit('close')">
    <div class="container">
      <div class="rule">
        <h2>RULES</h2>
       <button @click="$emit('close')">X</button>
      </div>
      <img src="../assets/images/image-rules.svg" alt="">
    </div>
  </div>
</template>
<script>

export default {
  props: ["isRules"],
  emits:['close'],
 
};
</script>

<style scoped>
h2,
button{
  font-size: 2rem;
}
h2{
  color: rgb(155, 168, 170);
}
button{
  border: none;
  appearance: none;
  background-color: transparent;
  color: grey;
  cursor: pointer;
}
button:hover,
button:active{
  color:black;
}
.rule{
  width: 100%;
  height: 3rem;
  display: flex;
  justify-content: space-between;
}
.container{
  padding: 2rem;
  width: 40%;
  height: 50%;
  background-color: rgb(255, 255, 255);
  border-radius: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.container img{
  width: 70%;
  margin-top: 2rem;
}
.modal{
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.3);
  z-index: 20;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
