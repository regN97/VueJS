<template>
  <h1>
    {{ greeting }}
  </h1>

  <button :title="buttonTitle" @click="changeGreeting">
    Click de thay doi
  </button>
</template>

<script setup>
import { ref } from 'vue'

const greeting = ref('Xin chao ban!')

const buttonTitle = ref('Nhan de thay doi loi chao')

const changeGreeting = () => {
  greeting.value = 'Hello World'
  buttonTitle.value = 'Loi chao moi da duoc cap nhat!'
}
</script>
