<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTarefas @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaFormulario v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxTarefa v-if="listaEstaVazia">
          Você nâo está muito produtivo hoje :(
        </BoxTarefa>
      </div>
    </div>
   
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefas from './components/FormularioTarefas.vue';
import TarefaFormulario from './components/TarefaFormulario.vue';
import ITarefa from './interfaces/ITarefa';
import BoxTarefa from '../src/components/BoxTarefa.vue'

export default defineComponent({
    name: "App",
    components: { 
      BarraLateral, 
      FormularioTarefas,
      TarefaFormulario,
      BoxTarefa 
    },
    data() {
      return {
        tarefas: [] as ITarefa[],
        modoEscuroAtivo: false
      }
    },
    computed: {
      listaEstaVazia(): boolean {
        return this.tarefas.length === 0;
      }
    },
    methods: {
      salvarTarefa(tarefa: ITarefa) {
        this.tarefas.push(tarefa);
      },
      trocarTema(modoEscuroAtivo: boolean) {
        this.modoEscuroAtivo = modoEscuroAtivo;
      }
    }
});
</script>

<style>
  .lista {
    padding: 1.25rem
  }

  main {
    --bg-primario: #FFF;
    --texto-primario: #000
  }

  main.modo-escuro {
    --bg-primario: #2B2D42;
    --texto-primario: #DDD
  }

  .conteudo {
    background-color: var(--bg-primario);
  }
</style>
