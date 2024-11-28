<template>
  <div class="container w-50">
    <h1 class="text-success">Conditional Rendering</h1>
    <p v-if="isActive">System is Active</p>
    <p v-else>System is unActive</p>

    <div>
      <p v-if="user.age > 30">{{ user.userName }} là trung niên</p>
      <p v-else-if="user.age >= 18">{{ user.userName }} là thanh niên</p>
      <p v-else>{{ user.userName }} là thiếu nên</p>
    </div>

    <div>
      <h3 class="text-success">Practice 1</h3>
      <p v-show="isVisible">Thông báo 1</p>
      <p v-show="!isVisible">Thông báo 2</p>
      <button class="btn btn-primary" @click="changeStatus">
        Change status
      </button>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const isActive = ref(true)
let isVisible = ref(true)

const user = reactive({
  userName: 'Trung',
  age: 31,
})

const changeStatus = () => {
  isVisible.value = !isVisible.value
}
</script>

<style lang="scss" scoped></style>
