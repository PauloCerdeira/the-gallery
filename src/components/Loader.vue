<template>
  <div class="loader-background">
    <div @click="toggleLoading()" class="loader-ball-container">
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
      loading: true,
    };
  },
  async created() {},
  mounted() {
   this.toggleLoading()
  },
  methods: {
    toggleLoading() {
      let ballContainer = document.getElementsByClassName(
        "loader-ball-container"
      )[0];
      let loaderBackground = document.getElementsByClassName(
        "loader-background"
      )[0];
      if (this.loading) {
        setTimeout(function() {
          ballContainer.classList.add("hidden");
        }, 1000);
        setTimeout(function() {
          loaderBackground.classList.add("hidden");
        }, 1500);
      } else {
        setTimeout(function() {
          ballContainer.classList.remove("hidden");
        }, 1500);
        setTimeout(function() {
          loaderBackground.classList.remove("hidden");
        }, 1000);
      }

      this.loading = !this.loading;
    },
  },
};
</script>

<style scoped>
.hidden {
  transform: scaleY(0%) !important;
}
.loader-background {
  transform-origin: 0% 100%;
  transition: transform ease-in-out 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  background: rgba(39, 39, 39, 0.603);
  height: 100%;
  width: 100%;
  z-index: 10;
}
.loader-ball-container {
  transform-origin: 0% 100%;
  transition: transform ease-in-out 0.2s;
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
