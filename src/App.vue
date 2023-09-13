<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    tarefaTemp : '',
    filtro:'todas',
    tarefas:[
      {
        titulo:'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar SASS',
        finalizada: false,

      },
      {
        titulo: 'ir para academia',
        finalizada: false,

      },
    ]
  });
  const getTarefaPendente = () => {
      return estado.tarefas.filter(tarefa => !tarefa.finalizada )
  }
  const getTarefaFinalizada = () => {
      return estado.tarefas.filter(tarefa => tarefa.finalizada )
  }
  const getTarefaFiltradas =() => {
    const {filtro} = estado

    switch(filtro) {
      case 'pendentes':
        return getTarefaPendente();
      case 'finalizadas':
        return getTarefaFinalizada();
      default:
        return estado.tarefas
      
      
    }
  }
  const toggleEvent =(tarefa) =>{
    tarefa.finalizada = !tarefa.finalizada
  }
  
  const cadastrarTarefa = () => {
    estado.tarefas.push({
      titulo: estado.tarefaTemp,
      finalizada: false
    })
    estado.tarefaTemp = '';
  }


</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Minhas Tarefas</h1>
      <p>
        voce possui {{ getTarefaPendente().length }} tarefas pendentes 
      </p>
    </header>
    
    <form >
      <div class="row">
      <div class="col">
        <input type="text" placeholder="digite a descrição da tarefa"  class="form-control" v-model="estado.tarefaTemp" required>
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary" v-on:click="cadastrarTarefa">Cadastrar</button>
      </div>
      <div class="col-md-2" >
        <select class="form-control" v-model="estado.filtro">
          <option value="todas">todas Tarefas</option>
          <option value="pendentes">pendentes</option>
          <option value="finalizadas">finalizadas</option>
        </select>
      </div>
    </div></form>

    <form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in getTarefaFiltradas()">
        <input type="checkbox" @change="toggleEvent(tarefa)" :checked="tarefa.finalizada" :id="tarefa.titulo">
        <label :for="tarefa.titulo" :class="{done: tarefa.finalizada }"  class="ms-3">{{ tarefa.titulo }}</label>
      </li>
    </ul>
  </form>
  </div>
</template>

<style scoped>
.done{
  text-decoration: line-through;
}
</style>
