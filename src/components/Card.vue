<template>
  <div class="wrapperCard">
      <div class="card">
        <div class="container">
          <h4><b>John Doe</b></h4>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat. Duis aute irure dolor in
            reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
            pariatur.
          </p>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "Card",
};
</script>

<style scoped>
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