<template>
    <div class="container mt-5">
        <p>{{ count }}</p>
        <button class="btn btn-primary" @click="increment(1)">Tang 1</button>
        <button class="btn btn-primary" @click="increment(3)">Tang 3</button>
        <button class="btn btn-primary" @click="increment(5)">Tang 5</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';

    const count = ref(0);

    const increment = (param) => {
        count.value += param;
    }
</script>

<style lang="scss" scoped>

</style>