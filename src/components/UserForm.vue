<template>
  <form id="formContainer" @submit.prevent="onSubmit">
    <input class="txtInput" v-model="attempts" placeholder="Attempts" />
    <input class="txtInput" v-model="completions" placeholder="Completions" />
    <input class="txtInput" v-model="yardsGained" placeholder="Yards Gained" />
    <input
      class="txtInput"
      v-model="interceptions"
      placeholder="Interceptions"
    />
    <input class="txtInput" v-model="touchdowns" placeholder="Touchdowns" />
    <input class="txtInput" v-model="name" placeholder="Name" />
    <input class="txtInput" v-model="notes" placeholder="Notes" />
    <select id="qbType" v-model="league">
      <option>NFL</option>
      <option>NCAA</option>
    </select>
    <button id="btnCal" type="submit" value="Submit">Calculate</button>
  </form>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "UserForm",
  props: {
    players: Array,
  },
  data() {
    return {
      name: "",
      league: "NFL",
      notes: "",
      attempts: 0,
      completions: 0,
      yardsGained: 0,
      interceptions: 0,
      touchdowns: 0,
    };
  },
  methods: {
    calculateNFL(data) {
      const limit = 2.375;

      let compVar = (data.completions / data.attempts - 0.3) * 5;
      if (compVar > limit) {
        compVar = limit;
      }
      if (compVar < 0) {
        compVar = 0;
      }

      let yardsVar = (data.yardsGained / data.attempts - 3) * 0.25;
      if (yardsVar > limit) {
        yardsVar = limit;
      }
      if (yardsVar < 0) {
        yardsVar = 0;
      }

      let touchdownsVar = (data.touchdowns / data.attempts) * 20;
      if (touchdownsVar > limit) {
        touchdownsVar = limit;
      }
      if (touchdownsVar < 0) {
        touchdownsVar = 0;
      }

      let interceptionsVar = limit - (data.interceptions / data.attempts) * 25;
      if (interceptionsVar > limit) {
        interceptionsVar = limit;
      }
      if (interceptionsVar < 0) {
        interceptionsVar = 0;
      }

      return (
        ((compVar + yardsVar + touchdownsVar + interceptionsVar) / 6) *
        100
      ).toFixed(1);
    },

    calculateNCAA(data) {
      const yardFact = 8.4;
      const touchdownFact = 330;
      const completionFact = 100;
      const interceptionFact = 200;

      let yardsGainedInt = yardFact * data.yardsGained
      let touchdownInt = touchdownFact * data.touchdowns
      let completionInt = completionFact * data.completions
      let interceptionInt = interceptionFact * data.interceptions

      return (((yardsGainedInt + touchdownInt + completionInt) - interceptionInt) / data.attempts).toFixed(1)
    },

    onSubmit() {
      const id = uuidv4();

      let data = {
        name: this.name,
        notes: this.notes,
        league: this.league,
        attempts: this.attempts,
        completions: this.completions,
        yardsGained: this.yardsGained,
        interceptions: this.interceptions,
        touchdowns: this.touchdowns,
      };

      let quarterback = {
        name: this.name,
        notes: this.notes,
        league: this.league,
        id: id,
        qbr: 0,
      };
      if (data.league === "NFL") {
        quarterback.qbr = this.calculateNFL(data);
      } else {
        quarterback.qbr = this.calculateNCAA(data);
      }

      this.$emit("add:players", quarterback);
    },
  },
};
</script>

<style scoped>
#btnCal {
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