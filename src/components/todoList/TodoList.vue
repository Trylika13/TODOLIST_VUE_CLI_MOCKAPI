<script setup>
import TodoListAddForm from "./TodoListAddForm.vue";
import TodoListFooter from "./TodoListFooter.vue";
import Todo from "./Todo.vue";
</script>
<template>
  <section
    class="bg-white rounded-xl shadow ring-1 ring-gray-200/60 overflow-hidden"
    aria-labelledby="todo-heading"
  >
    <h2 id="todo-heading" class="sr-only">Todo list</h2>

    <!-- INPUT PRINCIPAL -->
    <TodoListAddForm />

    <!-- LISTE DES TODOS -->
    <ul class="m-4 divide-y divide-gray-200" role="list" aria-label="Todos">
      <!-- ITEM (exemple) -->
      <todo />
      <!-- Message si aucun todo (à gérer en Vue) -->
      <li
        class="px-4 py-6 sm:px-5 text-gray-400 italic text-center hidden"
        role="listitem"
      >
        No tasks yet.
      </li>
    </ul>

    <!-- FOOTER DE LISTE -->
    <TodoListFooter />
  </section>
</template>
<style scoped></style>
