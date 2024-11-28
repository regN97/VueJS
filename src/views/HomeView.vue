<!-- eslint-disable no-unused-vars -->
<script setup>
import FormEditModal from '@/components/FormEditModal.vue'
import FormModal from '@/components/FormModal.vue'
import instanceAxios from '@/utils/configAxios'
import { onMounted, provide, ref } from 'vue'

const students = ref([])
const editIdSelected = ref('')
const isShowModal = ref(false)

const deleteItem = async id => {
  try {
    const isDeleted = confirm('Are you sure')
    if (!isDeleted) return
    const deleteStudentResponse = await instanceAxios.delete(`students/${id}`)
    // fetchStudents()
    students.value = students.value.filter(student => student.id !== id)
  } catch (error) {
    console.log(error)
  }
}

const fetchStudents = async () => {
  try {
    const fetchStudentsResponse = await instanceAxios.get('students')
    students.value = fetchStudentsResponse.data
  } catch (error) {
    console.log('some thing wrong')
  }
}
const handleCreateStudent = async student => {
  try {
    const createStudentResponse = await instanceAxios.post('students', student)
    // fetchStudents();
    //  students.value = [...students.value, createStudentResponse.data]
    students.value.push(createStudentResponse.data)
  } catch (error) {
    console.log('some thing wrong')
  }
}
const handleUpdate = async student => {
  try {
    const updateStudentResponse = await instanceAxios.put(
      `students/${editIdSelected.value}`,
      student,
    )
    isShowModal.value = false
    // fetchStudents()
    students.value = students.value.map(item => {
      if (item.id === editIdSelected.value) {
        return updateStudentResponse.data
      }
      return item
    })
  } catch (error) {
    console.log(error)
  }
}
const handleEdit = id => {
  editIdSelected.value = id
  isShowModal.value = true
}
const handleClose = () => {
  isShowModal.value = false
}

onMounted(() => {
  fetchStudents()
})
</script>

<template>
  <main>
    <FormModal @submitForm="handleCreateStudent" />
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
            <button class="btn btn-danger mx-2" @click="deleteItem(id)">
              Delete
            </button>
            <button class="btn btn-primary mx-2" @click="handleEdit(id)">
              Edit
            </button>
            <RouterLink class="btn btn-success mx-2" :to="`/students/${id}`"
              >Detail</RouterLink
            >
          </td>
        </tr>
      </tbody>
    </table>

    <FormEditModal
      v-if="isShowModal"
      :editIdSelected="editIdSelected"
      :isShowModal="isShowModal"
      :handleClose="handleClose"
      @handleUpdate="handleUpdate"
    />
  </main>
</template>
