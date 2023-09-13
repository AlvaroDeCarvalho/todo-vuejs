<template>
    <form>
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in getTarefaFiltradas()">
                <input type="checkbox" @change="toggleEvent(tarefa)" :checked="tarefa.finalizada" :id="tarefa.titulo">
                <label :for="tarefa.titulo" :class="{ done: tarefa.finalizada }" class="ms-3">{{ tarefa.titulo }}</label>
            </li>
        </ul>
    </form>
</template>