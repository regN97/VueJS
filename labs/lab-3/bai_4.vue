<template>
    <div class="container">
        <h2>Quản lý sản phẩm</h2>

        <div class="mb-3">
            <label for="categoryFilter">Lọc theo danh mục</label>
            <select v-model="selectedCategory" class="form-select" id="categoryFilter">
                <option value="">Tất cả</option>
                <option value="Electronics">Electronics</option>
                <option value="Accessories">Accessories</option>
            </select>
        </div>

        <div class="alert alert-info">Tổng giá trị hàng tồn kho: {{ totalStockValue }} VND</div>

        <div class="row">
            <template v-for="product in filteredProducts" :key="product.id">
                <div class="col-md-4">
                    <div class="card">
                        <img :src="product.imageUrl" class="card-img-top">
                        <div class="card-body">
                            <h5 class="card-title">{{ product.name }} - {{ product.category }}</h5>
                            <p v-if="product.inStock" class="text-success">Còn hàng</p>
                            <p v-else class="text-danger">Hết hàng</p>
                            <p>Giá: {{ product.price }} VND</p>
                            <p>Mô tả: {{ product.description }}</p>
                        </div>
                    </div>
                </div>
            </template>
        </div>
    </div>
</template>

<script setup>
import { computed, reactive, ref } from 'vue';

    const selectedCategory = ref("");
    const products = reactive([
{
  id: 1,
  name: 'Laptop',
  price: 15000000,
  quantity: 5,
  category: 'Electronics',
  inStock: true,
  description: 'Laptop thế hệ mới',
  imageUrl:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
},
{
    id: 2,
  name: 'iPhone',
  price: 8000000,
  quantity: 15,
  category: 'Electronics',
  inStock: true,
  description: 'Điện thoại thông minh',
  imageUrl:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
},
{
    id: 3,
  name: 'Headphones',
  price: 2000000,
  quantity: 0,
  category: 'Accessories',
  description: 'Tai nghe chất lượng cao',
  inStock: false,
  imageUrl:
    'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
},
]);

const totalStockValue = computed(() => {
    return products.reduce((total, product) => {
        return product.inStock ? total + product.price * product.quantity : total;
    }, 0);
});

const filteredProducts = computed(() => {
    if (!selectedCategory.value) {
        return products;
    }
    return products.filter((products) =>
        products.category === selectedCategory.value
    );
});
</script>

<style lang="scss" scoped>

</style>