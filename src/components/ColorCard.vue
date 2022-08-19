<script setup lang="ts">
import { ref } from "vue";
const porps = defineProps<{ left: string; right: string }>();
const left = ref({
  background: porps.left,
  boxShadow: "1px 1px 1px 1px #111",
});
const right = ref({
  background: porps.right,
  boxShadow: "1px 1px 10px 1px #111",
});
</script>
<template>
  <div class="card">
    <div class="left float" :style="left">
      <div class="in_left in" :style="left">
        {{ left.background }}
      </div>
    </div>
    <div class="right float" :style="right">
      <div class="in_right in" :style="right">
        {{ right.background }}
      </div>
    </div>
    <!--
     -->
  </div>
</template>
<style scoped>
.card {
  margin: 10px;
  width: 300px;
  height: 400px;
  border-radius: 20px;
  display: flex;
  overflow: hidden;
  position: relative;
}
.right {
}
.float {
  /* float: left; */
  width: 150px;
  height: 100%;
}
.left {
}
.in {
  margin: 0 auto;
  line-height: 90px;
  text-align: center;
  font-size: 20px;
  z-index: 2;
  color: #fff;
  border-radius: 20px;
  box-sizing: border-box;
  transition: all 0.2s;
}
.in:hover {
  transform: scale(1.02);
  transition: all 0.2s;
}
.in_right {
  width: 260px;
  height: 170px;
  position: absolute;
  top: 210px;
  left: -130px;
}
.in_left {
  width: 260px;
  height: 170px;
  position: absolute;
  top: 20px;
  left: 20px;
}
</style>
