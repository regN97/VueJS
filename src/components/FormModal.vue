<template>
  <div>
    <div>
      <!-- Button trigger modal -->
      <button
        type="button"
        class="btn btn-primary"
        data-bs-toggle="modal"
        data-bs-target="#exampleModal"
      >
        Launch demo modal
      </button>

      <!-- Modal -->
      <div
        class="modal fade"
        id="exampleModal"
        tabindex="-1"
        aria-labelledby="exampleModalLabel"
        aria-hidden="true"
      >
        <div class="modal-dialog">
          <div class="modal-content">
            <form @submit.prevent="handleSubmit">
              <div class="modal-header">
                <h1 class="modal-title fs-5" id="exampleModalLabel">
                  Modal Create Student
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
                  <label for="name" class="form-label">Name</label>
                  <input
                    v-model="student.name"
                    class="form-control"
                    type="text"
                    name="name"
                    placeholder="Enter Name"
                  />
                </div>
                <div class="form-group">
                  <label for="mssv" class="form-label">Mssv</label>
                  <input
                    v-model="student.mssv"
                    class="form-control"
                    type="text"
                    name="mssv"
                    placeholder="Enter mssv"
                  />
                </div>
              </div>
              <div class="modal-footer">
                <button
                  type="button"
                  class="btn btn-secondary"
                  data-bs-dismiss="modal"
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
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['submitForm'])

const student = ref({
  name: '',
  mssv: '',
})

const handleSubmit = () => {
  emit('submitForm', student.value)
}
</script>

<style lang="scss" scoped></style>
