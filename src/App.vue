<template>
  <div id="app">
    <character-filter-form :characters="characters" />
  </div>
</template>

<script>
import { eventBus } from './main.js'
import CharacterListForm from './components/CharacterListForm.vue'

export default {
  name: 'app',
  data(){
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  mounted(){
    fetch('https://www.breakingbadapi.com/api/characters')
    .then(res => res.json())
    .then(characters => this.characters = characters)

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },
  components: {
    "character-filter-form": CharacterListForm
  }
}
</script>

<style>
div {
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
