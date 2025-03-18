<script setup>
const props = defineProps(['tarefas']);

const atualizaTarefa = (tarefa, evento) => {
  tarefa.finalizada = evento.target.checked;
};
</script>

<template>
  <ul class="list-group mt-4">
    <!-- Exibe a mensagem se não houver tarefas -->
    <li v-if="props.tarefas.length === 0" class="list-group-item">
      Não existe tarefa pendente.
    </li>

    <!-- Lista de tarefas -->
    <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
      <input
        @change="(evento) => atualizaTarefa(tarefa, evento)"
        :checked="tarefa.finalizada"
        :id="tarefa.titulo"
        type="checkbox"
      />
      <label
        :class="{ done: tarefa.finalizada }"
        class="ms-3"
        :for="tarefa.titulo"
      >
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>