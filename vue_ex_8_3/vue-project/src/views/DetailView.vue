<template>
  <main v-if="todo">
    <h1>할 일 상세</h1>
    <p>번호: {{ todo.id }}</p>
    <p>제목: {{ todo.work }}</p>
    <p>내용: {{ todo.content }}</p>
    <p>완료 여부: {{ todo.is_completed }}</p>
    <p>생성일: {{ todo.created_at }}</p>
  </main>
</template>

<script setup>
  import { ref, onMounted } from 'vue'
  import { useRoute } from 'vue-router'
  import axios from 'axios'
  import { useTodoStore } from '@/stores/todoStore'

  const BASE_URL = 'http://localhost:8000'

  const route = useRoute()
  const todo = ref(null)
  const store = useTodoStore()

  onMounted(() => {
    axios({
      method: 'get',
      url: `${store.BASE_URL}/api/v1/todos/${route.params.id}/`,
    })
      .then((res) => {
        todo.value = res.data
      })
      .catch(err => console.log(err))
  })
</script>