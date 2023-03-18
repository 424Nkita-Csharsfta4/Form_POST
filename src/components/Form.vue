<template>
    <form @submit.prevent="submitForm">
        <div>
            <label for="name">Имя:</label>
            <input type="text" id="name" v-model="name" />
        </div>
        <div>
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="email" />
        </div>
        <div>
            <label for="password">Пароль:</label>
            <input type="password" id="password" v-model="password" />
        </div>
        <div>
            <label for="gender">Пол:</label>
            <select id="gender" v-model="gender">
                <option value="male">Мужской</option>
                <option value="female">Женский</option>
            </select>
        </div>
        <button type="submit">Отправить</button>
    </form>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue';
import axios from 'axios';

export default defineComponent({
    name: 'FormComponent',
    setup() {
        const name = ref('');
        const email = ref('');
        const password = ref('');
        const gender = ref('male');

        const submitForm = () => {
            const data = {
                name: name.value,
                email: email.value,
                password: password.value,
                gender: gender.value,
            };
            axios.post('http://example.com/api/users', data)
                .then(response => {
                    console.log(response.data);
                })
                .catch(error => {
                    console.log(error.response.data);
                });

        };

        return {
            name,
            email,
            password,
            gender,
            submitForm,
        };
    },
});
</script>
<style lang="less" scoped>
.form {
    max-width: 200px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 5px;
}

.form-group {
    margin-bottom: 10px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input,
select {
    display: block;
    width: 40%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
    transition: border-color 0.3s ease-in-out;
}

input:focus,
select:focus {
    outline: none;
    border-color: #3498db;
}

button[type="submit"] {
    display: block;
    margin-top: 20px;
    padding: 10px;
    background-color: #3498db;
    color: #fff;
    font-size: 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out;
}

button[type="submit"]:hover {
    background-color: #2980b9;
}
</style>