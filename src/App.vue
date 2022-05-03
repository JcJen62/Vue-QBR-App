<template>
  <h1>QBR App</h1>
  <helper-para />
  <user-form @add:players='addQuarterback' />
  <card :players="quarterbacks" @edit:players='editNotes' @delete:players='deleteQB'/>
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
    },

    editNotes(id, notes) {
      const newNotes = notes
      this.quarterbacks = this.quarterbacks.map(elm => {
        if (elm.id === id){
          elm.notes = newNotes
        }

        return elm
      })
    },

    // deleteQB(id) {

    // }
  }
};
</script>

<style>
h1 {
  text-align: center;
}

#app {
  max-width: 1200px;
  margin: 0 auto;
  width: 50%;
}
</style>
