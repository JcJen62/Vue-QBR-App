<template>
  <form id="formContainer">
    <input class="txtInput" v-model="text" placeholder="Attempts">
    <input class="txtInput" v-model="text" placeholder="Completions">
    <input class="txtInput" v-model="text" placeholder="Yards Gained">
    <input class="txtInput" v-model="text" placeholder="Interceptions">
    <input class="txtInput" v-model="text" placeholder="Touchdowns">
    <input class="txtInput" v-model="text" placeholder="Name">
    <input class="txtInput" v-model="text" placeholder="Notes">
    <select id="qbType">
      <option>NFL</option>
      <option>NCAA</option>
    </select>
    <button id="btnCal" type="submit">Calculate</button>
  </form>
</template>

<script>

export default {
  name: "UserForm",
}
</script>

<style scoped>
  #btnCal{
    width: 200px;
    margin: 8px;
  }

  #qbType {
    width: 200px;
    margin: 8px;
  }

  #formContainer {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    margin: 1rem;
    justify-content: center;
  }

  .txtInput {
    width: 200px;
    margin: 8px;
  }
</style>