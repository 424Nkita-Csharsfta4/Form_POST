<template>
    <input type="text" 
    class="input" 
    placeholder="text"
    v-model="computedValue">
</template>
<script lang="ts" setup>
import {defineProps, defineEmits, computed} from "vue";

/**
 * Почитай
 * https://vuejs.org/guide/essentials/computed.html#basic-example
 * reactive по сути тот же ref, лучше юзай ref
 * Ну я почитаю) ok
 * Инпут закастоми less
 * 
 * Попробуй прокоментировать все что написал чтобы ты понял сам. 
 * Ну и чтобы я понял что ты понял
 * 
 * Еще прочитай:
 * https://vuejs.org/guide/components/v-model.html#component-v-model
 * 
 * ok)
 * Я всю документацию прочетаю)
 * Смысла нету), лучше постепенно. Пока на практике не закрепиш забудешь все
 * ну каждая темма прочтенная будет с практикой) Ну вот сделай то шо я говорю, а потом посмотрим
 * 
 * Я пошел, вечером если хочешь могу зайти
 * 
 * ok
 */
const emit = defineEmits<{
  (e: "update:modelValue", value: string): void;
}>();


const props = defineProps<{
    modelValue:string;
    type:string;
}>();

// Норм? сойдет
const computedValue  = computed ({
    get:() => props.modelValue,
    set:(value: string) => {
        emit('update:modelValue', value);
    }
});
</script>

<style lang="less" scoped>

</style>