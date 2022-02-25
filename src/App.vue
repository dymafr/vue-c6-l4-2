<template>
  <form @submit.prevent="ajoutTodo">
    <label for="add-todo">Ajouter une todo </label>
    <input v-model="tache" id="add-todo" placeholder="Tâche à effectuer..." />
    <button>Ajouter</button>
  </form>
  <ul>
    <template v-for="(todo, index) in todos" :key="todo.id">
      <li>
        {{ todo.titre }}
        <button @click="suppTodo(index)">Supprimer</button>
      </li>
    </template>
  </ul>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tache = ref('');
const todos = ref([
  {
    id: 1,
    titre: 'Apprendre HTML',
  },
  {
    id: 2,
    titre: 'Apprendre CSS et Sass',
  },
  {
    id: 3,
    titre: 'Apprendre JavaScript',
  },
  {
    id: 4,
    titre: 'Apprendre TypeScript',
  },
  {
    id: 5,
    titre: 'Apprendre Vue',
  },
]);
let nouvelleTacheId = 6;

function ajoutTodo() {
  todos.value.push({
    id: nouvelleTacheId++,
    titre: tache.value,
  });
  tache.value = '';
}

function suppTodo(index) {
  todos.value.splice(index, 1);
}
</script>

<style scoped lang="scss"></style>
