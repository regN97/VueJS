<template>
    <div class="container mt-5">
        <h2>Danh sách sản phẩm</h2>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Ảnh</th>
                    <th scope="col">Tên</th>
                    <th scope="col">Giá</th>
                    <th scope="col">Tình trạng</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="({ id, name, price, inStock, image }, index) in products" :key="id">
                    <th scope="row">{{ index + 1 }}</th>
                    <td><img :src="image" alt="product image" width="50" height="50"></td>
                    <td>{{ name }}</td>
                    <td>{{ price }}</td>
                    <td>
                        <span v-if="inStock" class="badge bg-success">Còn hàng</span>
                        <span v-else class="badge bg-danger">Hết hàng</span>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
import { reactive } from 'vue';

    const products = reactive([
{
  id: 1,
  name: 'Laptop',
  price: 100,
  quantity: 11,
  category: 'Điện tử',
  inStock: true,
  image:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
},
{
    id: 2,
  name: 'iPhone',
  price: 300,
  quantity: 15,
  category: 'Điện lạnh',
  inStock: true,
  image:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
},
{
    id: 3,
  name: 'G-shock',
  price: 500,
  quantity: 3,
  category: 'Điện tử',
  inStock: false,
  image:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
},
]);
</script>

<style scoped>

</style>