<template>
  <div class="form">
    <div class="form__upper-text">
      Текст перед полем ввода
    </div>
    <div class="center" :class="{'center_error': error}">
      <div class="form__label" :class="{'form__label-up': active || text}" >
        Название поля
      </div>
      <img src="/Load.png" class="form__loader" />
      <textarea v-model="text" class="form__input-text" @focus="active = true" @blur="active=false"></textarea>
    </div>
    <div class="bottom">
      <div v-if="error" class="form__error">Ошибка</div>
      <div class="form__text-length">{{ currentTextLength }}/1000</div>
      <div style="text-align: left;">
        <button @click="text = ''" class="form__clear">Очистить</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref, computed} from 'vue'

const active = ref(false)
const text = ref('')

const currentTextLength = computed(() => {
  return text.value.length
})

const error = computed(() => {
  return currentTextLength.value > 10 ? 'Error' : ''
})

</script>

<style lang="scss">
@import "./form.scss";
</style>