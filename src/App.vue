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
  <h1>You did it!</h1>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>
</template>

<style scoped></style>
