<template>
    <div class="input-wrapper">
        <label :for="name">{{ name }}</label>
        <div class="input-container">
            <input :type="type" :placeholder="placeholder" v-model="value" />
            <button v-if="showClearButton" class="clear-button" @click="clearInput">
                <i class="material-icons">clear</i>
            </button>
            <i v-if="icon" class="material-icons icon">{{ icon }}</i>
        </div>
    </div>
</template>
  
<script lang="ts">
import { defineComponent, PropType } from 'vue';

export default defineComponent({
    name: 'MyInput',
    props: {
        name: {
            type: String,
            required: true,
        },
        type: {
            type: String,
            default: 'text',
        },
        placeholder: {
            type: String,
            default: '',
        },
        icon: {
            type: String,
            default: '',
        },
        showClearButton: {
            type: Boolean,
            default: false,
        },
    },
    setup(props, { emit }) {
        const clearInput = () => {
            emit('update:modelValue', '');
        };

        return {
            value: '',
            clearInput,
        };
    },
});
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
  