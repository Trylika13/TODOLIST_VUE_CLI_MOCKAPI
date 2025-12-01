<script setup>
import { reactive, onMounted, computed } from "vue";
import DB from "@/services/DB";
import TodoListAddForm from "./TodoListAddForm.vue";
import TodoListFooter from "./TodoListFooter.vue";
import Todo from "./Todo.vue";

const props = defineProps({
  apiURL: { type: String, required: true },
});

const todos = reactive([]);

const notCompletedCount = computed(
  () => todos.filter((todo) => !todo.completed).length
);
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

const deleteOneById = async (id) => {
  DB.deleteOneById(id);
  todos.splice(
    todos.findIndex((todo) => todo.id === id),
    1
  );
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
      <todo
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @on-delete="deleteOneById($event)"
      />
    </ul>

    <!-- FOOTER DE LISTE -->
    <TodoListFooter :notCompletedCount="notCompletedCount" />
  </section>
</template>
<style scoped></style>
