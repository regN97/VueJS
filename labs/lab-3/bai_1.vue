<template>
    <div class="container">
        <div class="row">
            <div class="col-sm-3">
                <div class="card">
                  <img :src="product.imageUrl" alt="product" class="card-img-top" />
                  <div class="card-body">
                    <h5 class="card-title">{{ product.name }}</h5>
                    <p class="card-text">Giá: {{ product.price }}</p>
                    <p class="card-text">Số lượng: {{ product.quantity }}</p>
                    <p class="card-text">Danh mục: {{ product.category }}</p>
                    <span
                      class="badge"
                      :class="{
                        'bg-success': product.inStock,
                        'bg-danger': !product.inStock,
                      }"
                    >
                      {{ product.inStock ? 'Còn hàng' : 'Hết hàng' }}
                    </span>
                  </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script setup>
import { reactive } from 'vue'

const product = reactive({
  id: 1,
  name: 'Sản phẩm A',
  price: 500,
  quantity: 5,
  category: 'Điện tử',
  inStock: true,
  description: 'Mô tả A',
  imageUrl:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
})
</script>

<style lang="scss" scoped></style>
