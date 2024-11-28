<template>
  <div>
    <h3 class="text-center">{{ title }}</h3>
    <h3 class="text-center">{{ msg }}</h3>

    <table class="table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Mssv</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="{ id, name, mssv } in students" :key="id">
          <td>{{ id }}</td>
          <td>{{ name }}</td>
          <td>{{ mssv }}</td>
          <td>
            <button class="btn btn-danger" @click="handleDelete(id)">
              Delete
            </button>
            <button class="btn btn-primary">Edit</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { inject } from 'vue'

defineProps(['students', 'msg'])
// defineProps({
//     students: [
//         {
//             id: Number,
//             name: String,
//             mssv: String
//         }
//     ]
// })
// Nhận dữ liệu title, nếu ko có dữ liệu hiện thị tham số thứ 2
const title = inject('title', 'No title')

// định nghĩa
const emit = defineEmits(['deleteStudents'])
const handleDelete = id => {
  //kích hoạt
  emit('deleteStudents', id)
}
</script>

<style lang="scss" scoped></style>
