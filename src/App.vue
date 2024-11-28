<script setup>
// import { ref } from 'vue'
// import LifeCycle from './components/LifeCycle.vue'
// const isShow = ref(true)

// const changeStatus = () => {
//   isShow.value = !isShow.value
// }
</script>

<template>
  <!-- <div>
    <div v-if="isShow">
      <LifeCycle />
    </div>
    <button class="btn btn-success" @click="changeStatus">Change Status</button>
  </div> -->
  <RouterView />
</template>
