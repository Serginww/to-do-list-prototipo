<template>
    <div class="tile flex-centered" :class="{checked: tarefa.checked}">
        <dir class="tile-content">
            <div class="title-subtitle">{{ tarefa.description }}
                <div>{{ tarefa.checked }}</div>
        </div>
        <div class="tile-action">
            <button @click = "$emit('toggle', tarefa)" class="btn btn-primary"> 
            <span v-if="tarefa.checked">Desmarcar</span>
            <span v-else> Conlcuido</span>

            </button>

            <button @click ="$emit('remove', tarefa)" class="btn btn-error"> Remover </button>
        </div>
        </dir>
    </div>
</template>

<script>
export default {
    name: "ListaDeTarefas",
    

    props: {

        tarefa: {type: Object,required: true}
    }
};
</script>

<style scoped>
 .checked{
    text-decoration: line-through ;
    color: lightslategray;
 }
</style>
