<template>
  <v-app>
    <v-content>      
      <PokemonList/>
    </v-content>
  </v-app>
</template>

<script>

import PokemonList from './components/PokemonList'

export default {
  name: 'App',
  components: {

    PokemonList,
  },
  data () {
    return {
      //
    }
  }
}
</script>
