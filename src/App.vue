<template>
    <custom-button>
        Тестовая кнопка
        <span class="test" :style="{background: 'red'}">23542352</span>
    </custom-button>
    <Form @send-data-form="HandlerForm"/>
    {{ handstrike }}
    <custom-input  
    v-model="handstrike" />
    <custom-input  
    v-model="handstrike" />
    <custom-input  
    v-model="handstrike" />
    <button @click="Click" class="button">Обычная кнопка</button>
    <button @click="MinusClick" class="button">Не обычная кнопка</button>


    <custom-input-view 
      name="Input Name"
      type="text"
      placeholder="Input Placeholder"
      icon="search"
      showClearButton
      v-model="handinputvalue"
      :style="{color:'orange'}">
    </custom-input-view>
    <custom-button-view type="primary"><span :style="{background:'orange'}">Тут</span></custom-button-view>
    <custom-button-view type="secondary"><span :style="{background:'orange'}">Нажми</span></custom-button-view>

   <customInputErr/>

</template>

<script setup lang="ts">
import {ref} from "vue"
import Form from './components/Form.vue';
import customInputErr from "./Task/custom-input-err.vue";
const HandlerForm = (data: [string, string, string, string]) => {
    console.log(data);
}

const handstrike = ref("stroka");

const handinputvalue = ref();

/**Клик */
const Click = ()=>{
    console.log("Нажата кнопка")
    handstrike.value += "1";
}

const MinusClick = ()=>{
    handstrike.value = handstrike.value.slice(0,-1 );
}
</script>

<style lang="less">
.button{
    margin-top: 3em;
    margin-right: 2em;
    background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  font-size: 16px;

  &:hover {
    background-color: #0069d9;
    cursor: pointer;
  }
}
</style>
