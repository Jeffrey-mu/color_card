<template>
  <div class="app">
    <div class="header">
      Welcome to the color card and see if there is any color you like.
      <a href="https://github.com/Jeffrey-mu/color_card" target="blank"
        ><img src="./assets/github.png" alt=""
      /></a>
    </div>
    <div class="content">
      <ColorCard
        v-for="[left, right] in colorList"
        :left="left"
        :right="right"
        :key="left"
      />
    </div>
  </div>
</template>

<script setup name="IndexPage" lang="ts">
import { computed, ref } from "vue";
import ColorCard from "./components/ColorCard.vue";
function getColor() {
  var str = "#";
  var arr = [
    "0",
    "1",
    "2",
    "3",
    "4",
    "5",
    "6",
    "7",
    "8",
    "9",
    "A",
    "B",
    "C",
    "D",
    "E",
    "F",
  ];
  for (var i = 0; i < 6; i++) {
    var num = parseInt(Math.random() * 16 + "");
    str += arr[num];
  }
  return str;
}
const count = ref(100);
const colorList = computed(() => {
  return new Array(+count.value)
    .fill(new Array(2).fill(null))
    .map((el) => el.map((el: string) => (el = getColor())));
});
</script>
<style scoped>
img {
  width: 20px;
  height: 20px;
  margin: 20px 20px;
  cursor: pointer;
}
a {
  display: inline-block;
  height: 40px;
}
img:hover {
  transform: scale(1.07);
  border-radius: 50%;
  box-shadow: 1px 1px 8px 0px #111;
}
.header {
  justify-content: space-between;
  padding: 0 10px;
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  color: rgb(170, 12, 165);
  line-height: 40px;
  display: flex;
}
.app {
  overflow: hidden;
  width: 100%;
  height: 100vh;
  background: conic-gradient(
    from 192deg at 46.5% 42.58%,
    #fa8792 -54.94deg,
    #561bbe 28.29deg,
    #70e6fb 157.82deg,
    #fbf8b3 220.83deg,
    #fa8792 305.06deg,
    #561bbe 388.29deg
  );
}
.content {
  overflow: auto;
  width: 100%;
  height: calc(100vh - 40px);
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
