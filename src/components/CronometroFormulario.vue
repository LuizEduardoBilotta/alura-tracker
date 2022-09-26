<template>
  <section class="is-align-self-center">
    <strong class="display">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  const ONE_SECOND_IN_MILIS = 1000;

  export default defineComponent({
    name: 'CronometroFormulario',
    props: {
      tempoEmSegundos: {
        type: Number,
        default: 0
      }
    },
    computed: {
      tempoDecorrido(): string {
        return new Date(this.tempoEmSegundos * ONE_SECOND_IN_MILIS).toISOString().substring(11, 19);
      }
    }
  });
</script>

<style>
  .display {
    color: var(--texto-primario);
  }
</style>