<script setup>
const props = defineProps(['cadastraTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp'])
</script>

<template>
    <form  @submit.prevent="props.cadastraTarefa"  >
        <div class="row">
            <div class="col">
                <!-- Use v-model diretamente no campo de entrada -->
                <input type="text" placeholder="Digite a descrição da tarefa" class="form-control " 
                :value="props.tarefaTemp" @change="props.editaTarefaTemp"  required>
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select class="form-control" @change="props.trocarFiltro">
                    <option value="todas">Todas as Tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>