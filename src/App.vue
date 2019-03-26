<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <lista @contador="editaTexto" :array="'oie'"></lista>
    <p>{{ recebido }}</p>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import lista from './components/lista.vue'

export default {
  name: 'app',
  data: () => {
      return {
        recebido: undefined
      }
  },
  components: {
    HelloWorld,
    lista
  },
  methods: {
    editaTexto(e){
        this.recebido = 'o ultimo numero recebido dos filhos foi: ' + e;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
