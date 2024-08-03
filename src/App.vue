<script setup>
import { ref } from 'vue'

const drinksData = ref([
  {
    title: '珍珠奶茶',
    description: '香濃奶茶搭配QQ的珍珠',
    price: 50,
    stock: 20
  },
  {
    title: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18
  },
  {
    title: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34
  },
  {
    title: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10
  },
  {
    title: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25
  },
  {
    title: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20
  },
  {
    title: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18
  },
  {
    title: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20
  }
])
</script>

<template>
  <div id="app" class="container">
    <div v-for="(drink, i) in drinksData" :key="i">
      <div class="card" style="margin-bottom: 1.5rem;">
        <div class="card-body" style="border: solid 1px; padding: 2rem;">
          <div style="display:flex">
            <h2 class="card-title" style="margin-right: 10px;">{{ drink.title }}</h2>
            <button type="button">修改名稱</button>
          </div>
          <p class="card-text my-2">{{ drink.description }}</p>
          <p class="card-text mb-3">價格：{{ drink.price }}</p>
          <p class="card-text mb-3">庫存：{{ drink.stock }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>
