<script setup>

    const props = defineProps(['tarefasPendentes']);

</script>

<template>
        <!--MINHAS TAREFAS-->
        <header class="p-5 mb-4 mt-4 bg-minhasTarefas rounded-3">
            <h1>Minhas Tarefas</h1>
            <p>
                Você possui {{ props.tarefasPendentes }} tarefas.
            </p>
        </header>
</template>
