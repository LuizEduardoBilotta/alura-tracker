<template>
  <div class="box has-text-weight-bold" :style="estilos">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BoxTarefa',
  data() {
    return {
      estilos: {
        background: '#FAF0CA'
      }
    }
  }
});
</script>

/*
OBS: Utilizando uma outra forma para o CSS, assim podemos controlar propriedades CSS com o Javascript.
*/
