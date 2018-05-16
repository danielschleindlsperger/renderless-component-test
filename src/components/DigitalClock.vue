<template>
  <Clock>
    <span
      slot-scope="{ formattedTime }"
      class="digital-clock"
      v-text="formattedTime"
    />
  </Clock>
</template>

<script>
import Clock from './Clock';

export default {
  name: 'DigitalClock',
  components: {
    Clock,
  },
};
</script>

<style>
.digital-clock {
  font-size: 20px;
  font-family: monospace;
}
</style>
