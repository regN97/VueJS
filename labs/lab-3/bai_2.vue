<template>
    <div class="container">
        <div class="row">
            <div class="col-sm-3">
                <div class="card">
                    <img :src="product.imageUrl" class="card-img-top">
                    <div class="card-body">
                        <h5 class="card-title">{{ product.name }} - {{ product.category }}</h5>
                        <p v-if="product.quantity > 10" class="text-success">Số lượng lớn</p>
                        <p v-else-if="product.quantity > 0" class="text-warning">Số lượng vừa phải</p>
                        <p v-else class="text-danger">Hết hàng</p>
                        <p>Giá: {{ product.price }} VND</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { reactive } from 'vue';

    const product = reactive({
  id: 1,
  name: 'Sản phẩm A',
  price: 100,
  quantity: 11,
  category: 'Điện tử',
  inStock: true,
  description: 'Mô tả A',
  imageUrl:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
})
</script>

<style lang="scss" scoped>

</style>