<script setup>
const props = defineProps(['cadastraTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp']);
</script>

<template>
  <form @submit.prevent="props.cadastraTarefa">
    <div class="row">
      <div class="col">
        <input
          :value="props.tarefaTemp"
          @input="props.editaTarefaTemp"
          required
          type="text"
          class="form-control"
          placeholder="Digite aqui a descrição da tarefa"
        />
      </div>

      <div class="col-md-1">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>

      <div class="col-md-2">
        <select @change="props.trocarFiltro" class="form-select">
          <option value="todas">Todas tarefas</option>
          <option value="pendente">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>