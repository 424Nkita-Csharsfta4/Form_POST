<template>
  <div class='custom-input__wrap'>
    <input class="custom-input" 
    v-model="value" :type="type" :placeholder="placeholder"/>
  </div>
</template>

<script lang='ts' setup>
import {defineProps, defineEmits, computed} from "vue";

const emit = defineEmits<{
  /** Специальное событие для обновления v-model */
  (eventName: "update:modelValue", value: string): void;
}>();

const props = defineProps<{
  /** Для привязки v-model */
  modelValue: string;

  /** Передаем тип инпута */
  type?: string;

  placeholder?: string;

}>();

/** Значение для привязки v-model локально в этом компоненте */
const value = computed({
  /** То что мы вернем (берем из пропсов)*/
  get(){
    return props.modelValue;
  },
  /** То что мы записываем */
  set(value){
    /** Обновляем верхний v-model через спец. событие */
    emit("update:modelValue", value);
  }
})

</script>

<style lang='less' scoped>
.custom-input{
  padding: 10px;
  background-color: #2c9bf6;
  border: none;
  border-radius: 2px;
  outline: none;
  border-bottom: solid 1px #222;
}
</style>