<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
        <cronometroMain :tempoEmSegundos="tempoEmSegundos"/>
        <botaoIniciarFinalizar @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando"/>
        <botaoIniciarFinalizar @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando"/>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import cronometroMain from './cronometroMain.vue'
import botaoIniciarFinalizar from './botaoIniciarFinalizar.vue'

export default defineComponent({
    name: 'temporizadorMain',
    emits: ['aoTemporizadorFinalizado'],
    components:{
        cronometroMain,
        botaoIniciarFinalizar,
    },
    data () {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false,
        }
    },

    methods: {
        iniciar () {
            this.cronometroRodando = true;
            this.cronometro = setInterval (() => {
                this.tempoEmSegundos += 1
            }, 1000);
        },
        finalizar () {
            this.cronometroRodando = false;
            clearInterval (this.cronometro);
            this.$emit ('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        },
    }
})
</script>
