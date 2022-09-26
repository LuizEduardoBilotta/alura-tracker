<template>
  <div class="is-flex is-align-item-center is-justify-content-space-between">
    <CronometroFormulario 
      :tempoEmSegundos="tempoEmSegundos" 
    />
    <BotaoTemporizador 
      @click="iniciar" 
      :habilitarStartStop="habilitarStartStop"
      :texto="botaoIniciar.texto"
      :icone="botaoIniciar.icone"
      :id="botaoIniciar.id"
    />
    <BotaoTemporizador 
      @click="finalizar" 
      :habilitarStartStop="!habilitarStartStop"
      :texto="botaoFinalizar.texto"
      :icone="botaoFinalizar.icone"
      :id="botaoFinalizar.id"
    />
    
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import CronometroFormulario from './CronometroFormulario.vue';
  import BotaoTemporizador from './BotaoTemporizador.vue';

  const ONE_SECOND_IN_MILIS = 1000;

  export default defineComponent({
    name: 'TemporizadorTarefas',
    components: {
      CronometroFormulario,
      BotaoTemporizador
    },
    emits: ['AoFinalizarTemporizador'],
    data() {
      return {
        tempoEmSegundos: 0,
        cronometroId: 0,
        habilitarStartStop: false,
        botaoIniciar: {
          texto: 'Play',
          icone: 'fas fa-play',
          id: 'btn-start'
        },
        botaoFinalizar: {
          texto: 'Stop',
          icone: 'fas fa-stop',
          id: 'btn-stop'
        }
      }
    },
    methods: {
      iniciar(): void {
        this.habilitarStartStop = true;
        this.cronometroId = setInterval(() => {
          this.tempoEmSegundos += 1;
        }, ONE_SECOND_IN_MILIS);
      }, 

      finalizar(): void {
        this.habilitarStartStop = false;
        clearInterval(this.cronometroId);
        this.$emit('AoFinalizarTemporizador', this.tempoEmSegundos);
        this.tempoEmSegundos = 0;
      }
    }
  });
</script>
