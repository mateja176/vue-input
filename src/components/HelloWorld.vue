<script setup lang="ts">
import { ComponentPublicInstance, computed, ref } from 'vue';

defineProps<{ msg: string; }>();

const inputRef = ref<HTMLInputElement | null>(null);
const valueRef = ref('');
const value = computed(() => {
  // return inputRef.value?.value;
  return valueRef.value;
});
const setInputRef = (e: Element | ComponentPublicInstance | null) => {
  if (!(e instanceof HTMLInputElement)) {
    return;
  }
  inputRef.value = e;
};
const onInput = (e: Event) => {
  if (!(e.target instanceof HTMLInputElement)) {
    return;
  }
  valueRef.value = e.target.value;
};
</script>

<template>
  <input :ref="setInputRef" @input="onInput" />
  <div>Value: {{ value }}</div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
