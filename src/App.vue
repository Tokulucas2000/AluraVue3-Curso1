<script lang="ts">
//Here we import the components that we want to use in the App.vue file
//Here we give a name to the variable that will receive the components for example Banner, ConteudoPrincipal, Rodape
import Banner from './components/Banner.vue';
import ConteudoPrincipal from './components/ConteudoPrincipal.vue';
import Rodape from './components/Rodape.vue';


export default {
  //If the variable name is the same as the component name, we can use the shorthand syntax, else we use the long syntax -> components: { Banner: Banner }
  components: { Banner, ConteudoPrincipal, Rodape }
}
</script>

<template>
<!-- Here the components is called to show on the page  -->
  <Banner />
  <ConteudoPrincipal />
  <Rodape />
</template>
