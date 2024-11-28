<template>
  <div>
    <BookCreate @submitForm="handleCreateBook" />
    <div class="container m-5">
      <h1>Danh sách sách</h1>
      <table class="table table-bordered">
        <thead>
          <tr>
            <th>ID</th>
            <th>Tiêu đề</th>
            <th>Tác giả</th>
            <th>Năm xuất bản</th>
            <th>Ảnh bìa</th>
            <th>Thao tác</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="{ id, title, author, year, cover } in books" :key="id">
            <td>{{ id }}</td>
            <td>{{ title }}</td>
            <td>{{ author }}</td>
            <td>{{ year }}</td>
            <td>{{ cover }}</td>
            <td>
              <button @click="deleteBook(id)" class="btn btn-danger mx-2">
                Xóa
              </button>
              <button @click="handleEdit(id)" class="btn btn-primary mx-2">
                Sửa
              </button>
              <RouterLink class="btn btn-success mx-2" :to="`/books/${id}`"
                >Xem</RouterLink
              >
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <BookEdit
      v-if="isShowModal"
      :editIdSelected="editIdSelected"
      :isShowModal="isShowModal"
      :handleClose="handleClose"
      @handleUpdate="handleUpdate"
    />
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import BookCreate from './BookCreate.vue'
import instanceAxios from '@/utils/configAxios'
import BookEdit from './BookEdit.vue'

const books = ref([])
const editIdSelected = ref('')
const isShowModal = ref(false)

const fetchBooks = async () => {
  try {
    const fetchBooksResponse = await instanceAxios.get('books')
    books.value = fetchBooksResponse.data
  } catch (error) {
    console.error(error)
  }
}

const handleCreateBook = async book => {
  try {
    await instanceAxios.post('books', book)
    fetchBooks()
  } catch (error) {
    console.error(error)
  }
}

const deleteBook = async id => {
  try {
    const isDeleted = confirm('Are you sure?')
    if (!isDeleted) return
    const deleteBookResponse = await instanceAxios.delete(`books/${id}`)
    books.value = books.value.filter(book => book.id !== id)
  } catch (error) {
    console.error(error)
  }
}

const handleEdit = id => {
  editIdSelected.value = id
  isShowModal.value = true
}

const handleClose = () => {
  isShowModal.value = false
}

const handleUpdate = async book => {
  try {
    const updateBookResponse = await instanceAxios.put(
      `books/${editIdSelected.value}`,
      book,
    )
    isShowModal.value = false
    books.value = books.value.map(item => {
      if (item.id === editIdSelected.value) {
        return updateBookResponse.data
      }
      return item
    })
  } catch (error) {
    console.error(error)
  }
}

onMounted(() => {
  fetchBooks()
})
</script>

<style lang="scss" scoped></style>
