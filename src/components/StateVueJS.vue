<template>
  <div>
    Notification: {{ notification }}
    <button @click="changeNoti">Change status</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const notification = ref("offline")
const changeNoti = () => {
  notification.value = "online"
}
</script>
<style lang="scss" scoped></style>
