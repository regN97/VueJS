<template>
  <div>
    <div class="">
      <h3 class="text-center">{{ message }}</h3>
      <button class="btn btn-primary" @click="handleChange">
        Change message
      </button>
    </div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, onUpdated, ref } from 'vue'

const message = ref('Hello World')

console.log('created')

const handleChange = () => {
  message.value = 'Life Cycle'
}

onMounted(() => {
  console.log('mounted')
})

onUpdated(() => {
  console.log('updated')
})

onUnmounted(() => {
  console.log('unmounted')
})
</script>

<style lang="scss" scoped></style>
