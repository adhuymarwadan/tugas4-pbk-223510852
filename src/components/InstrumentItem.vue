<template>
  <div class="instrument-item" @click="selectInstrument">
    <img :src="imageSrc" :alt="instrument.name" class="instrument-image" />
    <h3>{{ instrument.name }}</h3>
    <p>Type: {{ instrument.type }}</p>
    <p>Price: ${{ instrument.price }}</p>
  </div>
</template>

<script>
export default {
  props: {
    instrument: {
      type: Object,
      required: true,
    },
  },
  computed: {
    imageSrc() {
      return `https://via.placeholder.com/150?text=${this.instrument.name}`;
    },
  },
  methods: {
    selectInstrument() {
      this.$emit("instrument-selected", this.instrument);
    },
  },
};
</script>

<style scoped>
.instrument-item {
  cursor: pointer;
  padding: 15px;
  background-color: #f0f0f0;
  border-radius: 5px;
  transition: background-color 0.3s ease;
  text-align: center;
}

.instrument-item:hover {
  background-color: #e0e0e0;
}

.instrument-image {
  max-width: 100%;
  height: auto;
  margin-bottom: 10px;
}
</style>
