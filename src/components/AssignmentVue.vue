<template>
    <div>
        <div class="container my-3 form-control">
            <h3>Sinh viên</h3>
            <p>{{ student.name }}</p>
            <p>{{ student.age }}</p>
            <p>{{ student.class }}</p>
            <p>{{ student.gpa }}</p>
        </div>
        <div class="container my-3 form-control">
            <input class="form-control" v-model="student.name" type="text" placeholder="Nhập tên">
            <input class="form-control" v-model="student.age" type="text" placeholder="Nhập tuổi">
            <input class="form-control" v-model="student.class" type="text" placeholder="Nhập lớp">
            <input class="form-control" v-model="student.gpa" type="text" placeholder="Nhập điểm">
            <button class="btn btn-primary" @click="calculateYearOfBirth">Tính năm sinh</button>
        </div>
        <table class="container my-3 table table-bordered">
            <h3>Danh sách sinh viên</h3>
            <ul>
                <li v-for="student in webClass" :key="student">
                    <div>
                        <p>Tên: {{ student.name }}</p>
                        <p>Tuổi: {{ student.age }}</p>
                        <p>GPA: {{ student.gpa }}</p>
                        <button class="btn btn-primary" @click="showStudent(student)">Show</button>
                    </div>
                </li>
            </ul>
        </table>
    </div>
</template>

<script setup>
import { reactive, ref } from 'vue';

    const student = reactive({
        name: '',
        age: null,
        class: '',
        gpa: null,
    })

    const calculateYearOfBirth = () => {
        const yearOfBirth = new Date().getFullYear() - student.age;
        console.log(yearOfBirth);
    };

    const webClass = ref([
        {
            id: 1,
            name: 'Tran Duc Trung',
            age: 22,
            gpa: 7.5,
        },
        {
            id: 2,
            name: 'Nguyen Manh Toan',
            age: 20,
            gpa: 6.5,
        },
        {
            id: 3,
            name: 'Nguyen Duc Duy',
            age: 20,
            gpa: 8.5,
        },
    ]);

    const showStudent = (student) => {
            alert(`Tên: ${student.name} - GPA: ${student.gpa}`);
    }
</script>

<style scoped>

</style>