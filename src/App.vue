<script setup lang="ts">
import { ref, onMounted } from 'vue';
import axios from 'axios';

const message = ref<string>('백엔드에서 메시지를 가져오는 중...');

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:3000/api/hello'); 
    message.value = response.data;
  } catch (error) {
    console.error("API 호출 오류:", error);
    message.value = 'API 호출 실패: NestJS 서버를 확인하세요.';
  }
});
</script>

<template>
  <div style="padding: 20px; font-size: 24px; text-align: center;">
    <h1>분리형 풀스택 시연 (TypeScript)</h1>
    <p>받은 메시지: <strong style="color: #42b883;">{{ message }}</strong></p>
  </div>
</template>