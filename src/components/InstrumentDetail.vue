<template>
  <div v-if="instrument" class="instrument-detail">
    <h2>{{ instrument.name }}</h2>
    <p>Type: {{ instrument.type }}</p>
    <p>Price: ${{ instrument.price }}</p>
    <slot></slot>
    <button class="buy-button">Buy Now</button>
  </div>
  <div v-else>
    <p>Please select an instrument.</p>
  </div>
</template>

<script>
export default {
  props: {
    instrument: {
      type: Object,
      default: null,
    },
  },
};
</script>

<style scoped>
.instrument-detail {
  margin-top: 30px;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  text-align: left;
}

.buy-button {
  margin-top: 15px;
  padding: 10px 20px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.buy-button:hover {
  background-color: #2980b9;
}
</style>
