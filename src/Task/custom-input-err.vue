<template>
  <div class="input-field" :class="{ 'has-error': errorMessage }">
    <label :for="props.name">{{ props.label }} <span class="input-note">(Official e-mail address*)</span></label>
    <div class="input-wrapper">
      <input
       :id="props.name" 
       :name="props.name"
        v-model="modelValue"
         @input="onInput"
         placeholder="Official e-mail adress*" />
      <img v-show="!isValidEmail" src="https://cdn-icons-png.flaticon.com/512/1008/1008930.png" alt="">
    </div>
    <span class="error-message">{{ errorMessage }}</span>
  </div>
</template>

<script setup lang="ts">
import { computed, defineEmits, ref } from 'vue'

interface InputProps {
  name: string;
  label: string;
  value: string;
}

const props = defineEmits<InputProps>()

const modelValue = ref(props.value)
const isValidEmail = computed(() => {
  const email = (modelValue.value || '').trim()
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  return regex.test(email)
})

const onInput = (event: Event) => {
  const target = event.target as HTMLInputElement
  modelValue.value = target.value
}

const errorMessage = computed(() => {
  if (!isValidEmail.value) {
    return 'E-Mail address format invalid.'
  } else {
    return ''
  }
})
</script>

<style lang="less">
img {
  width: 20px;
  height: 20px;
}
.input-note {
  font-size: 12px;
  color: gray;
}


.input-field {
  position: relative;
  margin-bottom: 5em;
  margin-top: 5em;

  .input-wrapper {
    position: relative;

    input {
      width: 15%;
      padding: 10px 20px;
      font-size: 16px;
      line-height: 24px;
      color: #333;
      background-color: #fff;
      border: 1px solid #ddd;
      border-radius: 4px;

      &:focus {
        outline: none;
        border-color: #0078ff;
        box-shadow: 0 0 0 2px rgba(0, 120, 255, 0.25);
      }
    }

    img {
      position: absolute;
      left: 16%;
      top: 50%;
      transform: translateY(-50%);
      font-size: 18px;
      color: #ccc;
      cursor: pointer;

      &:hover {
        color: #999;
      }
    }
  }

  label {
    position: absolute;
    top: 10px;
    font-size: 16px;
    line-height: 24px;
    color: #666;
    transition: all 0.3s;
  }

  &.has-error {
    input {
      border-color: #ff4136;
    }

    .error-message {
      display: block;
    }

    label {
      color: #ff4136;
    }
  }

  .error-message {
    display: none;
    position: absolute;
    bottom: -20px;
    font-size: 14px;
    line-height: 20px;
    color: #ff4136;
  }
}
</style>
