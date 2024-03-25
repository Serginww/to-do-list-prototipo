<template>
  <div id="app">
    <div class="container grid-xs py-2">
      <img class="img-responsive" src="@/assets/lista.png" alt="coffetagrtodo">
      <form @submit.prevent="addTarefa(tarefa)">
        <div class="input-group">
          <input type="text" v-model="tarefa.description" class="form-input" placeholder="Adicionar uma tarefa">
          <button class="btn btn-success input-group-btn"><i class="icon icon-arrow-right"></i>Adicionar</button>
        </div>
      </form>
      <ul class="step">
        <li class="step-item active">
          <a href="#" class="tooltip" data-tooltip="Step 1">Step 1</a>
        </li>
        <li class="step-item active">
          <a href="#" class="tooltip" data-tooltip="Step 2">Step 2</a>
        </li>
        <li class="step-item">
          <a href="#" class="tooltip" data-tooltip="Step 3">Step 3</a>
        </li>
        <li class="step-item">
          <a href="#" class="tooltip" data-tooltip="Step 4">Step 4</a>
        </li>
      </ul>
    </div>
    <div class="tarefa-list">
      <tarefa v-for="t in tarefas" :key="t.id" @toggle ="toggleTarefa" @remove = "removeTarefa" :tarefa="t"></tarefa>
    </div>
  </div>
</template>

<script>
import Tarefa from './components/Tarefa'

export default {
  name: 'app',
  components: {
    Tarefa
  },
  data() {
    return {
      tarefas: [],
      tarefa: { description: '', checked: false }
    };
  },
  methods: {
    addTarefa(tarefa) {
      tarefa.id = Date.now();
      this.tarefas.push(tarefa);
      this.tarefa = { description: '', checked: false }; 
    },

      toggleTarefa(tarefa){
        const index = this.tarefas.findIndex(item => item.id === tarefa.id)
        if (index > -1){
          const checked = !this.tarefas[index].checked;
          this.tarefas[index].checked = checked;
        }
      },

      removeTarefa(tarefa){
        const index = this.tarefas.findIndex(item => item.id === tarefa.id)
          if (index > -1){
            this.tarefas.splice(index, 1);
          }
        }

  }
};
</script>

<style scoped>
img {
  max-width: 150px;
  margin: 0 auto;
}
.tarefa-list{
padding-top: 5rem;


}
</style>
