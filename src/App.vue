<!-- eslint-disable @typescript-eslint/no-unused-vars -->
<script setup lang="ts">
import { ref } from 'vue'

const tarefas = ref([
  { id: 1, texto: 'Estudar Vue 3', concluida: true },
  { id: 2, texto: 'Fazer exercícios', concluida: false },
  { id: 3, texto: 'Ler documentação', concluida: false },
])
const novaTarefa = ref('')

function adicionarTarefa() {
  if (novaTarefa.value.trim() !== '') {
    tarefas.value.push({
      id: Date.now(),
      texto: novaTarefa.value,
      concluida: false,
    })
    novaTarefa.value = ''
  }
}

function removerTarefa(id) {
  tarefas.value = tarefas.value.filter((tarefa) => tarefa.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Minha lista de tarefas</h1>
    <form @submit.prevent="adicionarTarefa">
      <input type="text" v-model="novaTarefa" placeholder="Adicione uma nova tarefa..." />
      <button type="submit">Adicionar</button>
    </form>

    <ul>
      <li v-for="tarefa in tarefas" :key="tarefa.id" :class="{ concluida: tarefa.concluida }">
        <input type="checkbox" v-model="tarefa.concluida" />
        <span>{{ tarefa.texto }}</span>
        <button @click="removerTarefa(tarefa.id)" class="remover">❌</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  max-width: 500px;
  margin: 2rem auto;
  padding: 1rem;
  font-family: sans-serif;
  background-color: #f4f4f4;
  border-radius: 8px;
}

h1 {
  text-align: center;
}

form {
  display: flex;
  margin-bottom: 1rem;
}

form input {
  flex: 1;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

form button {
  padding: 0.5rem 1rem;
  border: none;
  background-color: #41b883;
  color: white;
  border-radius: 4px;
  margin-left: 0.5rem;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  padding: 0.5rem;
  background-color: white;
  margin-bottom: 0.5rem;
  border-radius: 4px;
}

li.concluida span {
  text-decoration: line-through;
  color: #888;
}

li span {
  flex: 1;
  margin-left: 0.5rem;
}
.remover {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1rem;
}
</style>
