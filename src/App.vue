<template>
  <div id="app">
    <header class="header">
      <h1>Music Instrument Store</h1>
    </header>
    <div class="instrument-container">
      <InstrumentList
        :instruments="instruments"
        @instrument-selected="showInstrumentDetail"
      />
      <transition name="fade">
        <InstrumentDetail
          v-if="selectedInstrument"
          :instrument="selectedInstrument"
        >
          <template v-slot>
            <p>
              <strong>Additional Info:</strong> This instrument is not for
              begginers!
            </p>
          </template>
        </InstrumentDetail>
      </transition>
    </div>
  </div>
</template>

<script>
import InstrumentList from "./components/InstrumentList.vue";
import InstrumentDetail from "./components/InstrumentDetail.vue";

export default {
  name: "App",
  components: {
    InstrumentList,
    InstrumentDetail,
  },
  data() {
    return {
      instruments: [
        { id: 1, name: "Guitar", type: "String", price: 300 },
        { id: 2, name: "Piano", type: "Keyboard", price: 1500 },
        { id: 3, name: "Drums", type: "Percussion", price: 800 },
        { id: 4, name: "Violin", type: "String", price: 500 },
        { id: 5, name: "Flute", type: "Wind", price: 200 },
        { id: 6, name: "Saxophone", type: "Wind", price: 900 },
        { id: 7, name: "Trumpet", type: "Brass", price: 400 },
        { id: 8, name: "Clarinet", type: "Wind", price: 300 },
      ],
      selectedInstrument: null,
    };
  },
  methods: {
    showInstrumentDetail(instrument) {
      this.selectedInstrument = instrument;
    },
  },
};
</script>

<style>
#app {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  text-align: center;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.header {
  background-color: rgba(41, 128, 185, 0.9);
  color: #fff;
  padding: 20px 0;
  margin-bottom: 30px;
  width: 100%;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.instrument-container {
  width: 100%;
  max-width: 1200px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  justify-content: center;
}

.instrument-item {
  cursor: pointer;
  padding: 20px;
  background-color: rgba(255, 255, 255, 0.9);
  border-radius: 10px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.instrument-item:hover {
  background-color: rgba(236, 240, 241, 1);
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.instrument-image {
  max-width: 100%;
  height: auto;
  margin-bottom: 10px;
  border-radius: 10px;
}

.instrument-detail {
  margin-top: 30px;
  padding: 20px;
  background-color: #ecf0f1;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  text-align: left;
  animation: fadeIn 0.5s ease;
}

.instrument-detail h2 {
  color: #2c3e50;
  margin-bottom: 15px;
}

.instrument-detail p {
  color: #34495e;
  margin-bottom: 10px;
}

.additional-info {
  font-style: italic;
  color: #7f8c8d;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
