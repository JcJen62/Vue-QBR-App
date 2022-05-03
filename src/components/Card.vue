<template>
  <div class="wrapperCard">
      <div
        v-for="player in players"
        :key="player.id"
        class="card"
        >
        <div class="container">
          <h4><b>{{player.name}}</b></h4>
          <p>
            {{player.qbr}}<br>
            {{player.league}}<br>
            {{player.notes}}
          </p>
          <button class="cardBtn">Edit Notes</button>
          <button class="cardBtn">Delete QB</button>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "Card",
    props: {
      players: Array,
    }
};
</script>

<style scoped>
.cardBtn {
  
}

.wrapperCard {
  display: flex;
  flex-wrap: wrap;
}
.card {
  max-width: 23%;
  flex-basis: 100%;
  text-align: left;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.5s;
  margin: 15px 0.5rem 15px 0.5rem;
  border-radius: 6px;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.7);
}

.container {
  padding: 2px 16px;
}
</style>