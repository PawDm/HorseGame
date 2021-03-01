<template>
  <div class="v-main-wrapper">
    <h1>Проверим, сколько у вас будет лошадок.</h1>
    <button @click="startTimer" :disabled="isPlaying">Начать ловить</button>
    <v-timer v-if="showTimer" @start="start" />
    <div class="v-main-wrapper__area-for-horses">
      <v-horse
        v-for="horse in arrHorses"
        :key="horse"
        :idHorse="horse"
        @addScore="addScore"
      />
    </div>
    <v-result v-if="showResult" :score="score" />
  </div>
</template>

<script>
import vResult from './v-result.vue';
import vHorse from './v-horse.vue';
import vTimer from './v-timer.vue';
export default {
  name: 'v-main-wrapper',
  components: { vHorse, vResult, vTimer },
  data() {
    return {
      arrHorses: [],
      startCountOfHorse: 0,
      isPlaying: false,
      delay: null,
      score: 0,
      showResult: false,
      showTimer: false,
    };
  },
  methods: {
    startTimer() {
      this.showTimer = true;
    },
    start() {
      this.showTimer = false;
      this.startCountOfHorse = Math.floor(Math.random() * (20 - 10 + 1)) + 10;
      for (let i = 1; i < this.startCountOfHorse; i++) {
        this.arrHorses.push(i);
      }
      this.score = 0;
      this.showResult = false;
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      setTimeout(() => {
        this.arrHorses = [];
        this.isPlaying = false;
        this.showResult = true;
      }, this.delay);
    },
    addScore() {
      return this.score++;
    },
  },
};
</script>

<style>
.v-main-wrapper {
  max-width: 900px;
  margin: 0 auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #444;
}
.v-main-wrapper__area-for-horses {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 0 0 15px 0;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
