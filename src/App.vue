<template>
    <Form @send-data-form="HandlerForm"/>
    {{ value }}
    <custom-input v-model="value"/>
    <custom-input v-model="value"/>
</template>

<script setup lang="ts">
import {ref} from "vue"
import Form from './components/Form.vue';
const HandlerForm = (data: [string, string, string, string]) => {
    console.log(data);
}

const value = ref<string>("");
</script>

<style lang="less"></style>
