<template>
  <header>
    <nav>
      <RouterLink :to="{ name: 'TodoView' }" class="nav-link">
        할 일 목록으로 돌아가기
      </RouterLink>
    </nav>
  </header>
  <RouterView />
</template>

<script setup>
import { RouterView } from 'vue-router'
</script>

<style scoped>
</style>
