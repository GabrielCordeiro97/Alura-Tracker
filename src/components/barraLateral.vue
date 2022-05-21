<template>
    <div>
        <header>
            <h1>
                <img src="../assets/logo.png" alt="Logo Alura Track">
            </h1>
            <button class="button is-rounded is-link is-light" @click="ativaModoEscuro">
              Modo Escuro
            </button>
        </header>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'barraLateral',
    emits: ['ativa-modo-escuro'],
    methods: {
      ativaModoEscuro() : void {
        this.$emit('ativa-modo-escuro')
      }
    }
})
</script>

<style>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
