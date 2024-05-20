<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';


//OBJETO REATIVO
const estado = reactive ({
  filtro: 'todas',
  tarefaTemp: '',

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
      titulo: 'Ir para a academia',
      finalizada: true,
    }
  ]
});

//ATRIBUTOS
const getTarefasPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada);
};

const getTarefasFinalizadas = () => {
  return estado.tarefas.filter(tarefa => tarefa.finalizada);
};

const getTarefaFiltrada = () => {
  const { filtro } = estado;

  switch(filtro) {
    case 'pendentes':
      return getTarefasPendentes();
    case 'finalizada':
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;    
  }
};

const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  }
  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = '';
};
</script>

<template>
    <div class="container">
        <Cabecalho :tarefas-pendentes="getTarefasPendentes().length"/>
        <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefaTemp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastra-tarefa="cadastraTarefa"/>
        <ListaDeTarefas :tarefas="getTarefaFiltrada()"/>
    </div>
</template>

<style scoped>
.bg-minhasTarefas{
  background-color: #005366;
  color: #fff;
}

.done{
  text-decoration: line-through;
}
</style>