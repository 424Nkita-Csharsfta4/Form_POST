<template>
    <div class="input-wrapper">
        <input :type="type" :placeholder="placeholder" v-model="value" />
        <button v-if="showClearButton" class="clear-button" @click="clearInput">
            <i class="material-icons">clear</i>
        </button>
    </div>
</div></template>
<script lang="ts" setup>
import { defineProps, defineEmits, computed, ref } from "vue";

const showButton = ref(false);

const emit = defineEmits<{
    /** Специальное событие для обновления v-model */
    (eventName: "update:modelValue", value: string): void;
}>();

const props = defineProps<{
    /** Передаем тип инпута */
    type?: string;
    modelValue: string;
    placeholder?: string;
}>();


/** Значение для привязки v-model локально в этом компоненте */
const value = computed({
    /** То что мы вернем (берем из пропсов)*/
    get() {
        return props.modelValue;
    },
    /** То что мы записываем */
    set(value) {
        /** Обновляем верхний v-model через спец. событие */
        emit("update:modelValue", value);
    }
})
/**Очистка input */
const clearInput = () => {
    value.value = "";
};


const showClearButton = (): void => {
    if (value.value.length > 0) {
        showButton.value = true;
    } else {
        showButton.value = false;
    }
};


</script>
  
  
<style scoped>
.input-wrapper {
    display: flex;
    flex-direction: column;
    margin-bottom: 10px;
}

.input-container {
    display: flex;
    align-items: center;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 5px;
}

input {
    border: none;
    outline: none;
    flex-grow: 1;
}

.clear-button {
    background-color: transparent;
    border: none;
    outline: none;
    cursor: pointer;
    margin-left: 5px;
}

.icon {
    margin-right: 5px;
}
</style>
  