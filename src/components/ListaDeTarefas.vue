<script setup> 
    const props = defineProps(['tarefas', 'toggle'])
</script>

<template>
    <form>
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in props.tarefas">
                <input @change="props.toggle(tarefa)" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
                <label :for="tarefa.titulo" :class="{ done: tarefa.finalizada }" class="ms-3">{{ tarefa.titulo }}</label>
            </li>
        </ul>
    </form>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>