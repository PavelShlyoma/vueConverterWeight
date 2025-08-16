<script setup>
import {ref, computed} from 'vue'

const number = ref("")

const weightFrom = ref("gram")

const weightTo = ref("kilogram")

const weightList = {
  ton: 1000000,
  kilogram: 1000,
  gram: 1,
  milligram: 0.001,
  microgram: 0.000001,
  englishTon: 1016050,
  usTon: 907185,
  stone: 6350.29,
  lb: 453.592,
  ounce: 28.3495,
}

const total = computed(() => {
  let weight1 = weightList[weightFrom.value];
  let weight2 = weightList[weightTo.value];
  return (weight1 / weight2) * number.value;
})

const swapWeight = () => {
  let weight = weightTo.value;
  weightTo.value = weightFrom.value;
  weightFrom.value = weight;
}

</script>

<template>
  <div class="calculator-card">
    <h2 class="title">Конвертер величин</h2>

    <div class="input-group">
      <input v-model="number" type="number" id="amount-from" placeholder="Введите количество">
      <select v-model="weightFrom" id="from-unit">
        <option value="ton">Тонна</option>
        <option value="kilogram">Килограмм</option>
        <option value="gram">Грамм</option>
        <option value="milligram">Миллиграмм</option>
        <option value="microgram">Микрограмм</option>
        <option value="englishTon">Английская тонна</option>
        <option value="usTon">Американская тонна</option>
        <option value="stone">Стоун</option>
        <option value="lb">Фунт</option>
        <option value="ounce">Унция</option>
      </select>
    </div>

    <div class="swap-container">
      <button @click="swapWeight" class="swap-icon">⇅</button>
    </div>

    <div class="input-group">
      <input :value="total" type="number" id="amount-to" placeholder="Результат" readonly>
      <select v-model="weightTo" id="to-unit">
        <option value="ton">Тонна</option>
        <option value="kilogram">Килограмм</option>
        <option value="gram">Грамм</option>
        <option value="milligram">Миллиграмм</option>
        <option value="microgram">Микрограмм</option>
        <option value="englishTon">Английская тонна</option>
        <option value="usTon">Американская тонна</option>
        <option value="stone">Стоун</option>
        <option value="lb">Фунт</option>
        <option value="ounce">Унция</option>
      </select>
    </div>
  </div>
</template>

<style scoped>

.calculator-card {
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  padding: 25px;
  width: 350px;
}

.title {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
}

select, input {
  width: 100%;
  padding: 12px;
  margin-bottom: 15px;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 16px;
  box-sizing: border-box;
}

input {
  background-color: #f9f9f9;
}

.input-group {
  margin-bottom: 15px;
}

.swap-container {
  display: flex;
  justify-content: center;
  margin: 10px 0;
}

.swap-icon {
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s;
}

.swap-icon:hover {
  background-color: #45a049;
  transform: rotate(180deg);
}
</style>
