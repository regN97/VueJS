<template>
  <div>
    <!-- <slot name="header"></slot>
    <slot></slot>
    <slot name="footer"></slot> -->

    <slot :mes="message"></slot>
  </div>
</template>

<script setup>
const message = 'Gửi từ ChildrenSlot'
</script>

<style lang="scss" scoped></style>
