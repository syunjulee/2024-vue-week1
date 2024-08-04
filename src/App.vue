<script setup>
import { ref } from 'vue'

const drinksData = ref([
  {
    id: 1,
    title: '珍珠奶茶',
    description: '香濃奶茶搭配QQ的珍珠',
    price: 50,
    stock: 20
  },
  {
    id: 2,
    title: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18
  },
  {
    id: 3,
    title: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34
  },
  {
    id: 4,
    title: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10
  },
  {
    id: 5,
    title: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25
  },
  {
    id: 6,
    title: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20
  },
  {
    id: 7,
    title: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18
  },
  {
    id: 8,
    title: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20
  }
])

function handleDrinksStock(id, stock) {
  drinksData.value = drinksData.value.map((drink) => {
    if (drink.id === id) {
      drink.stock = stock
    }
    return drink
  })
}

const editDrinkID = ref(null)
const editDrinkTitle = ref('')

function startEdit(id, title) {
  editDrinkID.value = id
  editDrinkTitle.value = title
}

function saveTitle(id) {
  drinksData.value = drinksData.value.map((drink) => {
    if (drink.id === id) {
      drink.title = editDrinkTitle.value
    }
    return drink
  })
  editDrinkID.value = null
}

function cancelEdit() {
  editDrinkID.value = null
}
</script>

<template>
  <div id="app" class="container">
    <h1>2024 Vue 新手營作業 week 1</h1>
    <div v-for="drink in drinksData" :key="drink.id">
      <div class="card" style="margin-bottom: 1.5rem">
        <div class="card-body" style="border: solid 1px; padding: 2rem">
          <div style="display: flex">
            <h2 class="card-title" style="margin-right: 10px" v-if="editDrinkID !== drink.id">
              {{ drink.title }}
            </h2>
            <input
              v-else
              v-model="editDrinkTitle"
              @keyup.enter="saveTitle(drink.id)"
              @keyup.esc="cancelEdit"
              style="margin-right: 10px"
            />
            <button
              type="button"
              v-if="editDrinkID !== drink.id"
              @click="startEdit(drink.id, drink.title)"
            >
              修改名稱
            </button>
            <button type="button" v-else @click="saveTitle(drink.id)">儲存</button>
            <button type="button" v-if="editDrinkID === drink.id" @click="cancelEdit">取消</button>
          </div>
          <p class="card-text my-2">{{ drink.description }}</p>
          <p class="card-text mb-3">價格：{{ drink.price }}</p>
          <p class="card-text mb-3">
            庫存：
            <button
              @click="handleDrinksStock(drink.id, drink.stock - 1)"
              :disabled="drink.stock < 1"
            >
              -
            </button>
            {{ drink.stock }}
            <button @click="handleDrinksStock(drink.id, drink.stock + 1)">+</button>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>