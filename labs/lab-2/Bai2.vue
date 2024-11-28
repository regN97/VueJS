<template>
    <div class="container">
        <h1>Quản lý thông tin người dùng với reactive()</h1>
        <form class="form-control" @submit.prevent="submitForm">
            <label for="name">Tên:<input v-model="user.name"></label>
            <label for="age">Tuổi:<input type="number" v-model="user.age"></label>
            <label for="email">Email:<input v-model="user.email"></label>
            <button class="btn btn-primary mt-2" type="submit">Cập nhật</button>
        </form>
        <p>Tên: {{ user.name }}</p>
        <p>Tuổi: {{ user.age }}</p>
        <p>Email: {{ user.email }}</p>
    </div>
</template>

<script setup>
import { reactive } from 'vue';

    const user = reactive({
        name: "",
        age: null,
        email: "",
    })

    const submitForm = () => {
        if (user.name && user.email) {
            alert('Thông tin hợp lệ')
        } else {
            alert('Vui lòng nhập đầy đủ thông tin')
        }
    }
</script>

<style lang="scss" scoped>

</style>