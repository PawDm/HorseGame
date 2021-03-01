<template>
  <div class="v-result">
    <p class="rank">{{ rank }}</p>

    <img src="../assets/images/finish.png" alt="horse" />
    <p v-if="showFinish" class="finish">
      Вы будете прекрасным коневладельцем !
    </p>
  </div>
</template>

<script>
export default {
  name: 'v-result',
  props: ['score'],
  data() {
    return {
      rank: null,
      showFinish: false,
    };
  },
  mounted() {
    this.rank = `Поздравляем! У вас будет ${createStringForLastNumber(
      this.score
    )} !`;
    setTimeout(() => {
      this.showFinish = true;
    }, 1000);
  },
};

function createStringForLastNumber(countOfHorses) {
  let stringForHorse = '';
  if (countOfHorses > 10) {
    stringForHorse = 'лошадок';
  } else {
    let num = countOfHorses % 10;
    if (num > 1 && num < 5) {
      stringForHorse = 'лошадки';
    } else if (num == 1) {
      stringForHorse = 'лошадка';
    } else if (num > 4 || num == 0) {
      stringForHorse = 'лошадок';
    }
  }
  return countOfHorses + ' ' + stringForHorse;
}
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
  margin: 0 0 10px 0;
}
.v-result {
  max-width: 500px;
  margin: 0 auto;
}
.v-result img {
  width: 80%;
  margin: 0 0 1px 0;
}
.finish {
  margin: 5px 0 0 0;
  color: red;
  font-weight: bold;
  font-size: 2.4em;
}
</style>
