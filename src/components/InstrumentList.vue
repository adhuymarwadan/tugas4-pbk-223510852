<template>
  <div>
    <h2>Select an Instrument:</h2>
    <div class="instrument-list">
      <div
        v-for="instrument in instruments"
        :key="instrument.id"
        @click="selectInstrument(instrument)"
        class="instrument-item"
      >
        {{ instrument.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    instruments: {
      type: Array,
      required: true,
    },
  },
  methods: {
    selectInstrument(instrument) {
      this.$emit("instrument-selected", instrument);
    },
  },
};
</script>

<style scoped>
.instrument-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.instrument-item {
  cursor: pointer;
  padding: 10px 20px;
  margin: 5px;
  background-color: #f0f0f0;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.instrument-item:hover {
  background-color: #e0e0e0;
}
</style>
