<template>
  <div class="body-container">
    <div class="spinner">
      <div class="spinner__wrapper">
        <div
            v-for="(letter, index) in testVar"
            :key="index"
            :style="`--angleOffset:${index * -10}deg; --delayOffset:${index * 0.2}s;`"
            class="spinner-wheel">
          <span class="spinner-wheel__axis">
            {{letter}}
          </span>
          <span
              v-for="i in 5"
              :key="i"
              :class="`spinner-wheel__section--${i}`"
              class="spinner-wheel__section"
          >
            {{letter}}
          </span>
        </div>
      </div>
    </div>
    <div class="input spinner__input">
      <input
          value="defaultString"
          v-model="inputValue"
          class="name-input"
      >
    </div>
  </div>
</template>

<script setup lang="ts">
import {computed, ref} from "vue";

const inputValue = ref('');
const defaultString = "SpinSpinSpin"

const testVar = computed(
    () => inputValue.value.trim() ?
    inputValue.value.split('').filter((el) => el.trim()) :
    defaultString.toUpperCase().split('')
);

</script>

<style scoped>
@import "./style/spinner/component.scss";
</style>
