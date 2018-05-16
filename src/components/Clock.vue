<script>
export default {
  name: 'Clock',
  data() {
    return {
      date: this.getDate(),
    };
  },
  computed: {
    hours() {
      return this.date.getHours();
    },
    minutes() {
      return this.date.getMinutes();
    },
    seconds() {
      return this.date.getSeconds();
    },
    formattedTime() {
      return this.date.toLocaleTimeString();
    },
  },
  created() {
    this.updateDate();
  },
  methods: {
    getDate() {
      return new Date();
    },
    updateDate() {
      requestAnimationFrame(() => {
        this.date = this.getDate();
        this.updateDate();
      });
    },
  },
  render() {
    return this.$scopedSlots.default({
      date: this.date,
      hours: this.hours,
      minutes: this.minutes,
      seconds: this.seconds,
      formattedTime: this.formattedTime,
    });
  },
};
</script>