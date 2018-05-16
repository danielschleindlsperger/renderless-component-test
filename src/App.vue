<template>
  <div class="container">
    <div class="clocks">
      <h1>Clock components based on renderless data provider component</h1>
      <h2>Digital</h2>
      <DigitalClock />
      <h2>Analogue</h2>
      <AnalogueClock :size="300"/>
    </div>
  </div>
</template>

<script>
import DigitalClock from './components/DigitalClock';
import AnalogueClock from './components/AnalogueClock';

export default {
  name: 'App',
  components: {
    DigitalClock,
    AnalogueClock,
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  padding: 1rem;
  box-sizing: border-box;
}
.container * {
  box-sizing: inherit;
}
.clocks {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1, h2 {
  font-family: 'Helvetica Neue', Arial, sans-serif;
}
</style>
