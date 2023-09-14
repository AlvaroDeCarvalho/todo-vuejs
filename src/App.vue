<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue'
const estado = reactive({
    tarefaTemp: '',
    filtro: 'todas',
    tarefas: [
        {
            titulo: 'Estudar ES6',
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
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
}
const getTarefaFinalizada = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
}
const getTarefaFiltradas = () => {
    const { filtro } = estado

    switch (filtro) {
        case 'pendentes':
            return getTarefaPendente();
        case 'finalizadas':
            return getTarefaFinalizada();
        default:
            return estado.tarefas


    }
}

const cadastrarTarefa = () => {
    estado.tarefas.push({
        titulo: estado.tarefaTemp,
        finalizada: false
    })
    estado.tarefaTemp = '';
}

const toggleEvent = (tarefa) => {
    tarefa.finalizada = !tarefa.finalizada
}

</script>

<template>
    <div class="container">
        <Cabecalho 
        :tarefas-pendentes="getTarefaPendente().length" />

        <Formulario 
            :trocar-filtro="evento => estado.filtro = evento.target.value" 
            :tarefa-temp="estado.tarefaTemp" 
            :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" 
            :cadastra-tarefa="cadastrarTarefa"/>

        <ListaDeTarefas 
        :tarefas="getTarefaFiltradas()"
        :toggle="toggleEvent"/>
    </div>
</template>


