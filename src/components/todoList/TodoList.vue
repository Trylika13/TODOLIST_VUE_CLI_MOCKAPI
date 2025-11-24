<script setup>
import { reactive, onMounted } from "vue";
import DB from "@/services/DB";
import TodoListAddForm from "./TodoListAddForm.vue";
import TodoListFooter from "./TodoListFooter.vue";
import Todo from "./Todo.vue";

const props = defineProps({
  apiURL: { type: String, required: true },
});

const todos = reactive([]);

onMounted(async () => {
  DB.setApiURL(props.apiURL);
  todos.splice(todos.length, 0, ...(await DB.findAll()));
  console.table(todos);
});

// FUNCTION CRUD

const createItem = async (content) => {
  // 1. Lancer dans DB.create qui retounre la todo avec son id
  // On envoie le nouveau content à DB.create qui retourne un todo complet
  const todo = await DB.create(content);
  // 2. Ajouter cette todo dans todos
  todos.push(todo);
};
</script>
<template>
  <!-- CARD LISTE -->
  <section
    class="bg-slate-100 rounded-xl shadow ring-1 ring-slate-200/60 overflow-hidden"
    aria-labelledby="todo-heading"
  >
    <h2 id="todo-heading" class="sr-only">Todo list</h2>

    <!-- INPUT PRINCIPAL -->
    <TodoListAddForm @on-submit-add-form="createItem($event)" />

    <!-- LISTE DES TODOS -->
    <ul class="m-4 divide-y text-gray-600" role="list" aria-label="Todos">
      <!-- ITEM (exemple) -->
      <todo v-for="todo in todos" :key="todo.id" :todo="todo" />
    </ul>

    <!-- FOOTER DE LISTE -->
    <TodoListFooter />
  </section>
</template>
<style scoped></style>
