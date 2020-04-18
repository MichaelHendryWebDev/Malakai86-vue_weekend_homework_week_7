<template lang="html">
<form>
  <select v-on:change="handleSelect" v-model="selectedCharacter">
    <option disable value="">Select a Character</option>
    <option v-for="character in characters" :value="character">{{character.name}}</option>
  </select>
</form>
</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: "character-filter-form",
  data() {
    return {
      "search": "",
      "selectedCharacter": {},
    }
  },
  props: ["characters"],
  methods: {
    handleSelect() {
      this.search = ""
      eventBus.$emit('character-selected', this.selectedCharacter)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
