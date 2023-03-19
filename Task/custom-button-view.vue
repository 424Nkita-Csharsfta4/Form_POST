<template>
    <button  :class="['button', type]" >
        <slot>Click</slot>
    </button>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'MyButton',
    props: {
        type: {
            type: String,
            default: '',
        },
    },
});
</script>
<style lang="less">
.button {
    padding: 8px;
    background-color: #0077ff;
    border-radius: 4px;
    color: #fff;
    font-weight: bold;
    cursor: pointer;

    &:hover {
        background-color: #0059b3;
    }
}
</style>
  