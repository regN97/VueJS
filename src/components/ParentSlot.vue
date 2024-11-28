<template>
  <div>
    <div>
      <h3>Parent Slot</h3>
    </div>
    <ChildrenSlot v-slot="{ mes }">
      <!-- <template v-slot:header> header </template>
      <div>
        <h3>Children Slot</h3>
      </div>
      <template v-slot:footer> footer </template> -->
      <p>{{ mes }}</p>
    </ChildrenSlot>
  </div>
</template>

<script setup>
import ChildrenSlot from './ChildrenSlot.vue'
</script>

<style lang="scss" scoped></style>
