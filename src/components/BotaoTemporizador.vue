<template>
  <button class="button" :id="id" :disabled="habilitarStartStop">
    <span class="icon">
      <em :class="icone"></em>
    </span>
    <span>{{ texto }}</span>
  </button>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'BotaoTemporizador',
    props: {
      habilitarStartStop: {
        type: Boolean,
        default: false
      },
      texto: {
        type: String
      },
      id: {
        type: String
      },
      icone: {
        type: String
      }
    }
  });
</script>

<style>
  #btn-start {
    background-color: aquamarine;
  }

  #btn-stop {
    background-color: blueviolet;
  }
</style>