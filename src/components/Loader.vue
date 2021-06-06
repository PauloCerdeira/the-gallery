<template>
  <div v-if="loading" class="loader-background">
    <div class="loader-ball-container">
      <div class="loader-ball"></div>
      <div class="loader-ball"></div>
      <div class="loader-ball"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Loader",
  components: {},
  data() {
    return {
      loading: false,
    };
  },
  async created() {},
  methods: {
    toggleLoading() {
      this.loading = !this.loading;
    },
  },
};
</script>

<style scoped>
.loader-background {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  background: rgb(39, 39, 39);
  height: 100%;
  width: 100%;
  z-index: 10;
}
.loader-ball-container {
  display: flex;
  align-items: center;
  justify-content: center;
}
.loader-ball {
  margin: 10px;
  height: 20px;
  width: 20px;
  border-radius: 50%;
  background: white;
  animation-name: ball;
  animation-duration: 4s;
  animation-iteration-count: infinite;
}
@keyframes ball {
  0% {
    transform: scale(1);
  }
  25% {
    transform: scale(1.3);
  }
  50% {
    transform: scale(1.6);
  }
  75% {
    transform: scale(1.9);
  }
  100% {
    transform: scale(1);
  }
}
</style>
