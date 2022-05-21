<template>
    <boxVazio>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'tarefa sem descrição' }}
            </div>
            <div class="column">
                <cronometroMain :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </boxVazio>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import cronometroMain from './cronometroMain.vue'
import ITarefa from '../interface/ITarefa'
import boxVazio from './boxVazio.vue'

export default defineComponent({
    name: 'novaTarefa',
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        }
    },
    components: {
        cronometroMain,
        boxVazio,
    }
})
</script>

<style scoped>

</style>
