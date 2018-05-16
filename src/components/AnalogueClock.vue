<template>
  <Clock>
    <div
      slot-scope="props"
      class="digital-clock"
    >
    <svg
      :viewBox="viewBox"
      :width="size"
      :height="size"
      xmlns="http://www.w3.org/2000/svg"
    >
      <circle v-bind="backgroundCircle" fill="aquamarine"/>
      <rect v-bind="hourHand" :transform="hourTransform(props)" fill="black" />
      <rect v-bind="minuteHand" :transform="minuteTransform(props)" fill="black" />
      <rect v-bind="secondHand" :transform="secondTransform(props)" fill="black" />
    </svg>
    </div>
  </Clock>
</template>

<script>
import Clock from './Clock';

export default {
  name: 'AnalogueClock',
  components: {
    Clock,
  },
  props: {
    size: { type: Number, default: 100 },
  },
  computed: {
    viewBox() {
      const coords = [0, 0, this.size, this.size];
      return `${coords.join(' ')}`;
    },
    mid() {
      return this.size / 2;
    },
    backgroundCircle() {
      return { cx: this.mid, cy: this.mid, r: this.mid };
    },
    hourHand() {
      return this.clockHour(this.size * 0.2);
    },
    minuteHand() {
      return this.clockHour(this.size * 0.3);
    },
    secondHand() {
      return this.clockHour(this.size * 0.4);
    }
  },
  methods: {
    clockHour(length) {
      return {
        x: this.mid - 0.01 * this.mid,
        y: this.mid - length + 0.01 * this.mid,
        width: 0.01 * this.size,
        height: length,
      };
    },
    rotationFromPercentage(p) {
      return `rotate(${p * 360})`;
    },
    hourTransform({ hours, minutes, seconds }) {
      const secondsInHalfDay = 60 * 60 * 12;
      const hoursInSeconds =
        hours * 60 * 60 +
        minutes * 60 +
        seconds;
      return this.rotationFromPercentage(hoursInSeconds / secondsInHalfDay);
    },
    minuteTransform({ minutes, seconds }) {
      const secondsInHour = 60 * 60;
      const minutesInSeconds = minutes * 60 + seconds;
      return this.rotationFromPercentage(minutesInSeconds / secondsInHour);
    },
    secondTransform({ seconds }) {
      return this.rotationFromPercentage(seconds / 60);
    },
  },
};
</script>

<style scoped>
circle, rect {
  transform-origin: 50% 50%;
}
</style>
