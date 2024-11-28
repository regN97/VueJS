<template>
  <div>
    <div v-if="isShowModal" class="modal-backdrop fade show"></div>

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
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <form @submit.prevent="handleSubmit">
            <div class="modal-header">
              <h1 class="modal-title fs-5" id="exampleModalLabel">
                Modal Update Student
              </h1>
              <button
                type="button"
                class="btn-close"
                data-bs-dismiss="modal"
                aria-label="Close"
              ></button>
            </div>
            <div class="modal-body">
              <div class="form-group">
                <label for="name">Name</label>
                <input
                  type="text"
                  id="name"
                  class="form-control"
                  placeholder="Enter Name"
                  v-model="student.name"
                />
              </div>
              <div class="form-group">
                <label for="mssv">Mssv</label>
                <input
                  type="text"
                  id="mssv"
                  class="form-control"
                  placeholder="Enter Mssv"
                  v-model="student.mssv"
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
                Close
              </button>
              <button type="submit" class="btn btn-primary">
                Save changes
              </button>
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
const student = ref({
  name: '',
  mssv: '',
})
const fecthStudent = async () => {
  try {
    const response = await instanceAxios.get(`/students/${editIdSelected}`)
    console.log(response)

    student.value = response.data
  } catch (error) {
    console.log(error)
  }
}
const handleSubmit = () => {
  emit('handleUpdate', student.value)
}

onMounted(() => {
  fecthStudent()
})
</script>

<style lang="scss" scoped></style>
