<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

// var h = null;
// var d1 = null;
// var d2 = null;
var h = 10;
var d1 = 4;
var d2 = 3;

// var r1 = 4;
var r1 = ref(null);
var r2 = ref(null);
var l = ref(null);
var fai = ref(null);
var xita = ref(null);
function fixTail(num) {
  return Math.round(num * 100) / 100
}
function cal() {
  console.log(Math.pow((d1 - d2) / 2, 2))
  l.value = Math.sqrt(Math.pow((d1 - d2) / 2, 2) + Math.pow(h, 2));
  xita.value = Math.PI * (d1 - d2) / l.value;
  r1.value = Math.PI * d1 / xita.value;
  r2.value = r1.value - l.value;
  fai.value = xita.value / Math.PI * 180 ;

  // 对经过进行格式化
  r1.value = fixTail(r1.value);
  r2.value = fixTail(r2.value);
  l.value = fixTail(l.value);
  fai.value = fixTail(fai.value)+"°";
  xita.value = fixTail(xita.value);
  console.log(r1.value, r2.value, fai.value)
}


</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <div class="box">
      <img src="../assets/once_cup.svg">
      <table class="box">
        <tr>
          <td>纸杯高度(h):</td>
          <td><input v-model.number="h"></td>
        </tr>
        <tr>
          <td>杯口直径(d<sub>1</sub>):</td>
          <td><input v-model.number="d1"></td>
        </tr>
        <tr>
          <td>杯底直径(d<sub>2</sub>):</td>
          <td><input v-model.number="d2"></td>
        </tr>
        <tr>
          <td>
            <button id="submit" @click="cal">计算</button>
          </td>
        </tr>
        <tr>
          <td>外圆弧半径(r<sub>1</sub>):</td>
          <!-- <td><input id="r1" v-model.number="r1" readonly="readonly" placeholder="空" /></td> -->
          <td><input :value="r1" readonly="readonly" placeholder="空" /></td>
        </tr>
        <tr>
          <td>内圆弧半径(r<sub>2</sub>):</td>
          <td><input id="r2" v-model.number="r2" readonly="readonly" placeholder="空" /></td>
        </tr>
        <tr>
          <td>母线长度(l):</td>
          <td><input id="l" v-model.number="l" readonly="readonly" placeholder="空" /></td>
        </tr>
        <tr>
          <td>圆心角-弧度(θ):</td>
          <td><input id="xita" v-model.number="xita" readonly="readonly" placeholder="空" /></td>
        </tr>
        <tr>
          <td>圆心角-角度(φ/°):</td>
          <td><input :value="fai" readonly="readonly" placeholder="空" /></td>
        </tr>
        <tr>
          <td></td>
          <td></td>
        </tr>
      </table>
    </div>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
