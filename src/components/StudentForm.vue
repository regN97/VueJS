<template>
  <div class="container">
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th>STT</th>
          <th>ID</th>
          <th>Tên sinh viên</th>
          <th>MSSV</th>
          <th>Tên lớp</th>
          <th>Tương tác</th>
        </tr>
      </thead>
      <tbody v-if="students.length">
        <tr v-for="student in students" :key="student.id">
          <td>{{ students.indexOf(student) + 1 }}</td>
          <td>{{ student.id }}</td>
          <td>{{ student.name }}</td>
          <td>{{ student.mssv }}</td>
          <td>{{ student.className }}</td>
          <td>
            <button class="btn btn-warning" @click="editStudent(student)">Sửa</button>
            <button class="btn btn-danger" @click="deleteStudent(student.id)">Xóa</button>
          </td>
        </tr>
      </tbody>
      <tbody v-else>
        Không có sinh viên nào.
      </tbody>
    </table>
    <form class="form-control mt-5 w-50" @submit.prevent="addStudent">
      <div>
        <label class="form-label" for="">ID:</label>
        <input :value="studentId" @input="studentId = $event.target.value" class="form-control" type="text" name="id" />
      </div>
      <div>
        <label class="form-label" for="">Tên:</label>
        <input :value="studentName" @input="studentName = $event.target.value" class="form-control" type="text" name="name" />
      </div>
      <div>
        <label class="form-label" for="">MSSV:</label>
        <input :value="studentMssv" @input="studentMssv = $event.target.value" class="form-control" type="text" name="mssv" />
      </div>
      <div>
        <label class="form-label" for="">Lớp:</label>
        <select :value="studentClass" @change="studentClass = $event.target.value" class="form-select" name="className" id="className">
            <option value="1">WD19316</option>
            <option value="2">WD19317</option>
            <option value="3">WD19318</option>
        </select>
      </div>
      <template v-if="!isEditing">
          <button type="submit" class="btn btn-primary mt-3">Thêm sinh viên</button>
      </template>

      <template v-else>
          <button @click="updateStudent" type="submit" class="btn btn-primary mt-3">
              Cập nhật sinh viên
          </button>
      </template>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const students = ref([])
const studentId = ref('')
const studentName = ref('')
const studentMssv = ref('')
const studentClass = ref('')

const isEditing = ref(false)
const editingStudentId = ref(null)

const classes = {
    1: 'WD19316',
    2: 'WD19317',
    3: 'WD19318',
}

const addStudent = () => {
    if (
        !studentName.value ||
        !studentMssv.value ||
        !studentClass.value ||
        !studentId.value
    ) {
        return
    }

    const newStudent = {
        id: studentId.value,
        name: studentName.value,
        mssv: studentMssv.value,
        className: classes[studentClass.value],
    }
    students.value.push(newStudent)

    studentId.value = ''
    studentName.value = ''
    studentMssv.value = ''
    studentClass.value = ''
}

const deleteStudent = id => {
    if (confirm('Bạn chắc chắn xóa không?')) {
        students.value = students.value.filter(student => student.id !== id)
    }
}

const editStudent = student => {
    studentId.value = student.id
    studentName.value = student.name
    studentMssv.value = student.mssv
    studentClass.value = Object.keys(classes).find(
        key => classes[key] === student.className,
    )
    isEditing.value = true
    editingStudentId.value = student.id
}

const updateStudent = () => {
    const studentIndex = students.value.findIndex(
        student => student.id === editingStudentId.value
    )
    if (studentIndex !== -1) {
        students.value[studentIndex] = {
            id: studentId.value,
            name: studentName.value,
            mssv: studentMssv.value,
            className: classes[studentClass.value],
        }
    }
    clearForm()
}

const clearForm = () => {
    studentId.value = ''
    studentName.value = ''
    studentMssv.value = ''
    studentClass.value = ''
    isEditing.value = false
    editingStudentId.value = null
}
</script>

<style scoped></style>
