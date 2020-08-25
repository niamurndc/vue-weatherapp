<template>
  <div id="app">
    <Main />
  </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Main
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}

#app{
  background: url('./assets/bg.jpg') center center;
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  height: 100vh;
}

</style>
