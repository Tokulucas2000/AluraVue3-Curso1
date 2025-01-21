<script lang="ts">
import Tag from './Tag.vue';

export default {
  components: { Tag },
  props: {
    ingrediente: { type: String, required: true }
  },
  data() {
    return {
      selecionado: false
    }
  },
  methods: {
    aoClicar() {
      this.selecionado = !this.selecionado

      if (this.selecionado) {
        //Emit note
        // Emit the event to add the ingredient, present on the main component in this case ConteudoPrincipal.vue
        this.$emit('adicionarIngrediente', this.ingrediente)
      } else {
        this.$emit('removerIngrediente', this.ingrediente);
      }
    }
  },
  //Emit note
  //declaring all the events that will be emitted
  emits: ['adicionarIngrediente', 'removerIngrediente']
}
</script>

<template>
  <!-- The button bellow defines if the tag wil be "ativa" or not--> 
  <!-- The button will change the value of "selecionado" and will emit the event to add or remove the ingredient -->
  <button
    class="ingrediente"
    @click="aoClicar"
    
    :aria-pressed="selecionado"
  >
    <Tag :texto="ingrediente" :ativa="selecionado" />
  </button>
</template>

<style scoped>
.ingrediente {
  cursor: pointer;
}
</style>