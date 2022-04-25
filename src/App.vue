<template>
  <h1>QBR App</h1>
  <helper-para />
</template>

<script>
import HelperPara from './components/HelperPara.vue'

export default {
  name: 'App',
  components: {
    HelperPara
  }
}
</script>

<style>
  h1 {
    text-align: center;
  }

  #app {
    max-width: 960px;
    margin: 0 auto;
    width: 50%;
  }
</style>
