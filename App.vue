<template>
  <ul>
    <li v-for="character in characters" v-bind:key="character.name" >
        {{ character.name }}
    </li>
  </ul>
  
</template>

<script>


export default {
  data () {
      
    return {
      characters: []
    }
  },
  methods: {
    getCharacters() {
      fetch(process.env.VUE_APP_BASE_URL + process.env.VUE_APP_LIST_PATH)
      .then(response =>response.json()
        )
      .then(data => {
        this.characters = data.results
      })
    }
  },
mounted() {
  this.getCharacters()
},
  
  name: 'App',
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
