<template>
  <div class="container mt-5">
    <h1 class="text-center">Danh sach san pham</h1>
    <div class="row">
      <div class="col-sm-4">
        <div class="card">
          <img
            :src="products[0].image"
            alt="Hinh anh san pham"
            class="card-img-top"
          />
          <div class="card-body">
            <h3 class="card-title">{{ products[0].name }}</h3>
            <p class="card-text">{{ products[0].description }}</p>
            <p class="card-text">{{ products[0].price }}</p>
            <button class="btn btn-success">Mua ngay</button>
          </div>
        </div>
      </div>
      <div class="col-sm-4">
        <div class="card">
          <img
            :src="products[1]['image']"
            alt="Hinh anh san pham"
            class="card-img-top"
          />
          <div class="card-body">
            <h3 class="card-title">{{ products[1].name }}</h3>
            <p class="card-text">{{ products[1].description }}</p>
            <p class="card-text">{{ products[1].price }}</p>
            <button class="btn btn-success">Mua ngay</button>
          </div>
        </div>
      </div>
      <div class="col-sm-4">
        <div class="card">
          <img
            :src="products[2].image"
            alt="Hinh anh san pham"
            class="card-img-top"
          />
          <div class="card-body">
            <h3 class="card-title">{{ products[2].name }}</h3>
            <p class="card-text">{{ products[2].description }}</p>
            <p class="card-text">{{ products[2].price }}</p>
            <button class="btn btn-success">Mua ngay</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const products = [
  {
    name: 'San pham 1',
    description: 'Mo ta san pham 1',
    price: 500000,
    image:
      'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
  },
  {
    name: 'San pham 2',
    description: 'Mo ta san pham 2',
    price: 400000,
    image:
      'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
  },
  {
    name: 'San pham 3',
    description: 'Mo ta san pham 3',
    price: 600000,
    image:
      'https://fastly.picsum.photos/id/1/300/300.jpg?hmac=w1b4AOJM9vszS0a867iY2NXBzwc4LCeA0U6sEjdlSDk',
  },
]
</script>
