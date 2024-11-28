<template>
  <div class="m-5">
    <!-- Button trigger modal -->
    <button
      type="button"
      class="btn btn-primary"
      data-bs-toggle="modal"
      data-bs-target="#exampleModal"
    >
      Sửa sách
    </button>

    <!-- Modal -->
    <div
      class="modal fade"
      :class="isShowModal ? 'show' : ''"
      :style="isShowModal ? { display: 'block' } : { display: 'none' }"
      id="exampleModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <form @submit.prevent="handleSubmit">
            <div class="modal-header">
              <h1 class="modal-title fs-4" id="exampleModalLabel">Sửa sách</h1>
              <button
                type="button"
                class="btn-close"
                data-bs-dismiss="modal"
                aria-label="Close"
              ></button>
            </div>
            <div class="modal-body">
              <div class="form-group">
                <label for="title" class="h6 form-label">Tiêu đề</label>
                <input
                  v-model="books.title"
                  class="form-control"
                  name="title"
                  placeholder="Nhập tiêu đề..."
                  type="text"
                />
              </div>
              <div class="form-group">
                <label for="author" class="h6 form-label">Tác giả</label>
                <input
                  v-model="books.author"
                  class="form-control"
                  name="author"
                  placeholder="Nhập tác giả..."
                  type="text"
                />
              </div>
              <div class="form-group">
                <label for="year" class="h6 form-label">Năm xuất bản</label>
                <input
                  v-model="books.year"
                  class="form-control"
                  name="year"
                  placeholder="Nhập năm xuất bản..."
                  type="text"
                />
              </div>
              <div class="form-group">
                <label for="cover" class="h6 form-label">Ảnh bìa</label>
                <input
                  v-model="books.cover"
                  class="form-control"
                  name="cover"
                  placeholder="Nhập ảnh bìa..."
                  type="text"
                />
              </div>
            </div>
            <div class="modal-footer">
              <button
                type="button"
                class="btn btn-secondary"
                data-bs-dismiss="modal"
                @click="handleClose"
              >
                Hủy bỏ
              </button>
              <button type="submit" class="btn btn-primary">Sửa</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import instanceAxios from '@/utils/configAxios'
import { onMounted, ref } from 'vue'

const emit = defineEmits(['handleUpdate'])

const { editIdSelected } = defineProps([
  'isShowModal',
  'handleClose',
  'editIdSelected',
])

const books = ref({
  title: '',
  author: '',
  year: '',
  cover: '',
})

const fetchBook = async () => {
  try {
    const response = await instanceAxios.get(`/books/${editIdSelected}`)
    books.value = response.data
  } catch (error) {
    console.error(error)
  }
}

const handleSubmit = () => {
  emit('handleUpdate', books.value)
}

onMounted(() => {
  fetchBook()
})
</script>

<style lang="scss" scoped></style>
