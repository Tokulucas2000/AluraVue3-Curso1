<script lang="ts">
export default {
  props: {
    texto: { type: String, required: true },
    ativa: Boolean // default value is false
  }
}
</script>

<template>
  <!-- Applyng css with condition -->
  <!-- Applyng css based on ativa bool value, definig if the class will be "tag" or "tag.ativa" -->
  <span :class="['tag', { ativa }]">
    {{ texto }}
  </span>
</template>

<style scoped>
.tag {
  display: inline-block;
  border-radius: 0.5rem;
  min-width: 4.25rem;
  padding: 0.5rem;
  text-align: center;
	transition: 0.2s;
  color: var(--cinza);
  background: var(--cinza-claro);
  font-weight: 400;
}

.tag.ativa {
  color: var(--creme, #FFFAF3);
  background: var(--coral, #F0633C);
  font-weight: 700;
}
</style>