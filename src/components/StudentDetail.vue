<template>
  <div>
    <div>
      <h3>Student Detail</h3>
      <div>
        <p>{{ student.name }}</p>
        <p>{{ student.mssv }}</p>
        <p></p>
      </div>
    </div>
  </div>
</template>

<script setup>
import instanceAxios from '@/utils/configAxios'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'

const { params } = useRoute()
const student = ref({})
const fetchStudent = async () => {
  const fetchStudentsResponse = await instanceAxios.get(`students/${params.id}`)
  student.value = fetchStudentsResponse.data
}

onMounted(() => {
  fetchStudent()
})
</script>

<style lang="scss" scoped></style>
