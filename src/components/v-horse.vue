<template>
  <div class="v-horse" @click="getHorse">
    <img
      :class="{ invisible: showBlock }"
      src="../assets/images/horse.png"
      alt="horse"
    />
  </div>
</template>

<script>
export default {
  name: 'v-horse',
  props: ['idHorse'],
  data() {
    return {
      showBlock: false,
    };
  },
  methods: {
    getHorse() {
      this.showBlock = true;
      this.$emit('addScore');
    },
  },
};
</script>

<style>
.v-horse {
  cursor: pointer;
  flex-basis: 25%;
}
.v-horse img {
  width: 100%;
}
.invisible {
  display: none;
}
</style>
