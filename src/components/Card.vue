<template>
  <div id="box">
    <div class="wrapperCard">
      <div v-for="player in players" :key="player.id" class="card">
        <div class="container">
          <h4>
            <b>{{ player.name }}</b>
          </h4>
          <p>
            QBR: {{ player.qbr }}<br />
            {{ player.league }}<br />
            Notes: {{ player.notes }}
          </p>

          <input v-model="notes" id="editNote" placeholder="Your new note"/>
          <button class="cardBtn">Save New Note</button>
          <button class="cardBtn">Edit Notes</button>
          <button class="cardBtn">Delete QB</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    players: Array,
  },
};
</script>

<style scoped>
.cardBtn {
  margin: 8px;
  border: none;
  padding: 10px;
  border-radius: 5px;
  background-color: darkslategray;
  color: white;
}

#editNote {
  margin: 8px;
  width: 50%;
  padding: 8px;
}

#box {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
}

.wrapperCard {
  display: flex;
  flex-wrap: wrap;
}
.card {
  max-width: 30%;
  flex-basis: 100%;
  text-align: left;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.5s;
  margin: 15px 0.5rem 15px 0.5rem;
  border-radius: 6px;
  background-color: white;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.7);
}

.container {
  padding: 2px 16px;
}
</style>