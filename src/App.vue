<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuro}">
    <div class="column is-one-quarter">
      <barraLateral @ativa-modo-escuro="inserirModoEscuro" />
    </div>
    <div class="column is-three-quarter conteudo">
      <formularioPrincipal @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <novaTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <boxVazio v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </boxVazio>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import barraLateral from './components/barraLateral.vue';
import formularioPrincipal from './components/formularioPrincipal.vue';
import novaTarefa from './components/novaTarefa.vue';
import ITarefa from './interface/ITarefa'
import boxVazio from './components/boxVazio.vue'


export default defineComponent({
  name: 'App',
  data () {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false,
    }
  },
  components: {
    barraLateral,
    formularioPrincipal,
    novaTarefa,
    boxVazio,
  },
  computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    inserirModoEscuro() {
      this.modoEscuro = !this.modoEscuro
    },
  },
});
</script>

<style>

.lista {
  padding: 1.5rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
