<script setup>
  import { reactive } from 'vue';
  import {Cabecalho} from './components/Cabecalho.vue'
  import {Formulario} from './components/Formulario.vue';
  
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
      <Cabecalho  />
      <Formulario />
    <!-- <ListaDeTarefas /> -->
  </div>
</template>

<style scoped>
.done{
  text-decoration: line-through;
}
</style>
