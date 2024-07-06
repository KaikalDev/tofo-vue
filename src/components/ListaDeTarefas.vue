<script setup>
const props = defineProps(['tarefas', 'existeTarefas']);
</script>

<template>
    <span v-if="props.existeTarefas" class="aviso">Adicione uma tarefa</span>
    <ul v-else class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
.aviso {
    font-size: 34px;
    margin-top: 24px;
}

.done {
    text-decoration: line-through;
}
</style>