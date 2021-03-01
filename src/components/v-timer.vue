<template>
  <div class="v-timer">
    <p v-if="currentTime != 0">Начинаем через</p>
    <p>{{ currentTime }}</p>
  </div>
</template>

<script>
export default {
  name: 'v-timer',
  data() {
    return {
      timer: null,
      currentTime: 3,
    };
  },
  mounted() {
    this.startTimer();
  },
  methods: {
    startTimer() {
      this.currentTime = 3;
      this.timer = setInterval(() => {
        this.currentTime--;
      }, 1000);
    },
    stopTimer() {
      clearTimeout(this.timer);
      this.$emit('start');
    },
  },
  watch: {
    currentTime(time) {
      if (time === 0) {
        this.stopTimer();
      }
    },
  },
};
</script>

<style>
.v-timer {
}
.v-timer p {
  margin: 0 0 5px 0;
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
