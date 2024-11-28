<template>
  <div>
    <div class="container m-5 w-50">
      <h2>Chi tiết sách</h2>
      <div class="row">
        <label class="form-label h5" for="title">Tiêu đề</label>
        <p class="form-control">{{ book.title }}</p>
      </div>
      <div class="row">
        <label class="form-label h5" for="author">Tác giả</label>
        <p class="form-control">{{ book.author }}</p>
      </div>
      <div class="row">
        <label class="form-label h5" for="year">Năm xuất bản</label>
        <p class="form-control">{{ book.year }}</p>
      </div>
      <div class="row">
        <label class="form-label h5" for="cover">Ảnh bìa</label>
        <p class="form-control">{{ book.cover }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import instanceAxios from '@/utils/configAxios'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'

const { params } = useRoute()
const book = ref({})

const fetchBook = async () => {
  const fetchBooksResponse = await instanceAxios.get(`books/${params.id}`)
  book.value = fetchBooksResponse.data
}

onMounted(() => {
  fetchBook()
})
</script>

<style lang="scss" scoped></style>
