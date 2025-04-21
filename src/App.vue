<script setup lang="ts">
import Toast from './components/Toast.vue'
import { ref } from 'vue'

const toastRef = ref()

function showCustomToast() {
  toastRef.value?.showToast('This is a custom toast!', 3000)
}
</script>

<template>
  <button @click="showCustomToast">Show Toast</button>
  <Toast ref="toastRef" />
</template>
