<template>
    <div>
        <h2>Form Binding</h2>

        <form action="">
            <div class="form-group">
                <label for="email">Email</label>
                <input type="text" v-model="email">
            </div>
            <div class="form-group">
                <label for="contact">Contact: </label>
                <textarea placeholder="Please contact" v-model="contact"></textarea>
            </div>
            <div class="form-group">
                <label for="term">Term:</label>
                <input type="checkbox" v-model="isChecked">
            </div>
            <div class="form-group">
                <label for="html">html:</label>
                <input type="checkbox" v-model="courseName" value="html">
            </div>
            <div class="form-group">
                <label for="css">css:</label>
                <input type="checkbox" v-model="courseName" value="css">
            </div>
            <p>{{ email }}</p>
            <p>{{ contact }}</p>
            <p>{{ isChecked }}</p>
            <p>{{ courseName }}</p>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';

    const email = ref('');
    const contact = ref('');
    const isChecked = ref(false);
    const courseName = ref([]);
</script>

<style scoped>

</style>