<script setup lang="ts">
import { ref, onMounted } from 'vue'

const visible = ref(false)
const message = ref('')

function showToast(text: string, duration = 3000) {
  message.value = text
  visible.value = true
  setTimeout(() => {
    visible.value = false
  }, duration)
}

// Expose globally if needed
defineExpose({ showToast })
</script>

<template>
  <div
    v-if="visible"
    class="toast-notify"
  >
    {{ message }}
  </div>
</template>

<style scoped>
.toast-notify {
  position: fixed;
  bottom: 1.5rem;
  right: 1.5rem;
  background: #333;
  color: white;
  padding: 1rem 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
  animation: fadeInOut 3s ease;
}
@keyframes fadeInOut {
  0% { opacity: 0; transform: translateY(20px); }
  10% { opacity: 1; transform: translateY(0); }
  90% { opacity: 1; transform: translateY(0); }
  100% { opacity: 0; transform: translateY(20px); }
}
</style>
