<template>
  <div>
    <h1>List Rendering</h1>
  </div>
  <div>
    <h3>v-for with array</h3>
    <ul v-for="(food, index) in foods" :key="food">
      <li>{{ index }} - {{ food }}</li>
    </ul>
  </div>
  <div>
    <h3>v-for with object</h3>
    <ul v-for="{ id, userName, address } in users" :key="id">
      <li>{{ id }} - {{ userName }} - {{ address }}</li>
    </ul>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const foods = reactive(['rice', 'noodle', 'pizza'])

const users = reactive([
  {
    id: 1,
    userName: 'John',
    address: 'Ha Noi',
  },
  {
    id: 2,
    userName: 'Doe',
    address: 'Da Nang',
  },
])
</script>

<style lang="scss" scoped></style>
