<template>
  <div>
    <p :class="active">{{ name }}</p>
    <input type="text" v-model="name">
  </div>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('TDT');
const active = ref('text-danger');
</script>

<style lang="scss" scoped></style>
