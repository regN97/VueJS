<template>
    <div class="container">
        <h1>Quản lý giỏ hàng với ref()</h1>
        <p>Số lượng sản phẩm: {{ productCount }}</p>
        <button @click="icreaseCount">Tăng</button>
        <button @click="decreaseCount" :disabled="productCount === 0">Giảm</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';

    const productCount = ref(0);
    const icreaseCount = () => {
        productCount.value++;
    }

    const decreaseCount = () => {
        if (productCount.value > 0) {
            productCount.value--;
        }
    }
</script>

<style lang="scss" scoped>

</style>