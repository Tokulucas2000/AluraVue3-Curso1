<script lang="ts">
import type ICategoria from '@/interfaces/ICategoria';
import type { PropType } from 'vue';
import Tag from './Tag.vue';
import IngredienteSelecionavel from './IngredienteSelecionavel.vue';

export default {
  props: {
    //Definig the type of categoria based on ICategoria
    //Importing component #2
    categoria: { type: Object as PropType<ICategoria>, required: true }
  },
  components: { Tag, IngredienteSelecionavel },
  emits: ['adicionarIngrediente', 'removerIngrediente']
}
</script>

<template>
  <article class="categoria">
    <header class="categoria__cabecalho">
      <!-- importing image src must have the bind, so use ":src" -->
      <img :src="`/imagens/icones/categorias_ingredientes/${categoria.imagem}`" alt="" class="categoria__imagem">

      <h2 class="paragrafo-lg categoria__nome">{{ categoria.nome }}</h2>
    </header>

    <ul class="categoria__ingredientes">
      <!-- Understanding v-for -->
      <!-- v-for is necessary to run the entire list in this case the list is "ingrediente" and ":key" is a unique identifier for each element -->
      <!-- The key must be a primitive value for example a string or a int -->
       <!-- Importing component #3 -->
       <li v-for="ingrediente in categoria.ingredientes" :key="ingrediente"> 
        <!-- Using the data saved on categoria imported from the SelecionarIngredientes -->
         <!-- $event to acess the event that was sending -->
       <IngredienteSelecionavel
          :ingrediente="ingrediente"          
          @adicionar-ingrediente="$emit('adicionarIngrediente', $event)"
          @remover-ingrediente="$emit('removerIngrediente', $event)"
        />
      </li>
    </ul>
  </article>
</template>

<style scoped>
.categoria {
  width: 19.5rem;
  padding: 1rem;
  border-radius: 1rem;
  background: var(--branco, #FFF);
  box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.categoria__cabecalho {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.categoria__imagem {
  width: 3.5rem;
}

.categoria__nome {
  text-align: center;
  color: var(--verde-medio, #3D6D4A);
  font-weight: 700;
}

.categoria__ingredientes {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}
</style>