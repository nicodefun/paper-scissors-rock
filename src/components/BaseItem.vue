<template>
  <button :class="isBattle ? 'battle' : 'btn'">
    <div class="border" :class="color" :id="id"></div>
    <img class="icon" :src="src" alt="" />
  </button>
</template>
<script>
export default {
  props: ["color", "src", "isRules", "id", "isBattle"],
};
</script>
<style scoped>
button {
  position: relative;
  background: #fff;
  border-radius: 999px;
  border: none;
  border-top: 1.3rem solid rgb(238, 238, 238);
  border-bottom: 1rem solid rgb(200, 200, 200);
  z-index: 10;
}
.btn {
  width: 8rem;
  height: 8.2rem;
}
.battle {
  width: 15rem;
  height: 15rem;
}
.battle img.icon {
  width: 40%;
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.btn img.icon {
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.battle .border {
  width: 15rem;
  height: 15.3rem;
}
.btn .border {
  width: 8rem;
  height: 8.3rem;
}
.border {
  position: absolute;
  top: -1.3rem;
  left: 0;
  border-radius: 999px;
  z-index: 100;
}
.btn .red{
  border: 1rem solid rgba(249, 33, 0, 0.803);
}
.battle .red {
  border: 2rem solid rgba(249, 33, 0, 0.803);
}
.btn .yellow{
  border: 1rem solid rgba(228, 190, 0, 0.803);
}
.battle .yellow {
  border: 2rem solid rgba(228, 190, 0, 0.803);
}
.btn .blue{
  border: 1rem solid rgba(0, 46, 228, 0.882);
}
.battle .blue {
  border: 2rem solid rgba(0, 46, 228, 0.882);
}
</style>
