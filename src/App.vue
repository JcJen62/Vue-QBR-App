<template>
  <h1>QBR App</h1>
  <helper-para />
  <user-form @add:players='addQuarterback' />
  <card :players="quarterbacks" />
</template>

<script>
import HelperPara from "./components/HelperPara.vue";
import UserForm from "./components/UserForm.vue";
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    HelperPara,
    UserForm,
    Card,
  },
  data() {
    return {
      quarterbacks: [
        {
          name: "Tom Brady",
          qbr: "102.1",
          notes: "Goat",
          league: "NFL",
          id: "1",
        },
        {
          name: "Cam Rising",
          qbr: "84.2",
          notes: "Utah QB",
          league: "NCAA",
          id: "2",
        },
      ],
    };
  },
  methods: {
    addQuarterback(quarterback) {
      this.quarterbacks.push(quarterback)
    }
  }
};
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
