<script setup>
import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "@/components/AppFooter.vue";
import TodoList from "@/components/todoList/TodoList.vue";
</script>

<template>
  <AppHeader />
  <main class="w-full max-w-xl mt-10 bg-white rounded-xl">
    <TodoList apiURL="https://691b336c2d8d78557571fc4d.mockapi.io/" />
  </main>
  <AppFooter />
</template>

<style scoped></style>
