<template>
  <header class="is-flex is-flex-direction-column is-align-items-center">
    <h1>
      <img src="../assets/logo-alura-tracker.png" alt="">
    </h1>
    <button class="button" @click="alterarTema">
     {{ textoBotao }}
    </button>
  </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    computed: {
      textoBotao() {
        if (this.modoEscuroAtivo) {
          return 'Desativar modo escuro';
        }
        return 'Ativar modo escuro';
      }
    },
    data() {
      return {
        modoEscuroAtivo: false
      }
    },
    methods: {
      alterarTema() {
        this.modoEscuroAtivo = !this.modoEscuroAtivo;
        this.$emit('aoTemaAlterado', this.modoEscuroAtivo);
      }
    }
  });
</script>

<style scoped>
  header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
  }

  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>