<script setup>
    const props = defineProps(['cadastraTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp']);
</script>

<template>
<!--FORMULÁRIO DE TAREFAS-->
    <form @submit.prevent="props.cadastraTarefa">
        <div class="row">
            <!--Coluna 1-->
            <div class="col">
                <input
                    :value="props.tarefaTemp"
                    @change="props.editaTarefaTemp"
                    required
                    type="text"
                    placeholder="Digite a descrição da tarefa:"
                    class="form-control"
                />
            </div>
            <!--Coluna 2-->
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <!--Coluna 3-->
            <div class="col-md-2">
                <select @change="props.trocarFiltro">
                    <option value="todas">Todas as Tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizada">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>
