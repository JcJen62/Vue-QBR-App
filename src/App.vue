<template>
  <h1>QBR App</h1>
  <helper-para />
  <user-form />
</template>

<script>
import HelperPara from './components/HelperPara.vue'
import UserForm from './components/UserForm.vue'

export default {
  name: 'App',
  components: {
    HelperPara,
    UserForm
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
