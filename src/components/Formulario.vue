<script setup>
    const props = defineProps(['cadastrarTarefa','tarefaTemp','filtro'])
</script>

<template>
    <form>
        <div class="row">
            <div class="col">
                <input type="text" placeholder="digite a descrição da tarefa" class="form-control" v-model="props.tarefaTemp" required>
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary" v-on:click="props.cadastrarTarefa">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select class="form-control" v-model="props.filtro">
                    <option value="todas">todas Tarefas</option>
                    <option value="pendentes">pendentes</option>
                    <option value="finalizadas">finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>