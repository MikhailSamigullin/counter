<template>
  <div class="counter">
    <div class="count">
      <div :class="{ active_count: isRun }">
        {{ hours }}{{ minutes }}{{ seconds }}
      </div>
    </div>
    <div class="buttons">
      <div v-if="isRun" @click="pauseTimer" class="button pause"></div>
      <div
        v-else
        @click="startTimer"
        :class="{ active: isRun }"
        class="button play"
      ></div>
      <div
        @click="resetTimer"
        :class="{ active: isRun }"
        class="button stop"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CounterComponent",
  data() {
    return {
      time: 0,
      currentTime: null,
      isRun: false,
    };
  },
  computed: {
    mSeconds() {
      return this.time * 1000;
    },
    seconds() {
      let sec = Math.floor(this.mSeconds / 1000);
      sec = sec % 60;
      if (sec < 10 && this.minutes) {
        return `0${sec}`;
      }
      return sec;
    },
    minutes() {
      let min = Math.floor((this.time % 3660) / 60);
      if (min === 0) {
        return null;
      }
      if (min < 10 && this.hours) {
        return `0${min}:`;
      }
      if (min < 60) {
        return `${min}:`;
      }
      return `00:`;
    },
    hours() {
      let hour = Math.floor(this.time / 3660);
      if (hour === 0) {
        return null;
      } else {
        return `${hour}:`;
      }
    },
  },
  methods: {
    startTimer() {
      this.isRun = true;
      this.timerInterval = setInterval(() => (this.time += 1), 1000);
    },
    pauseTimer() {
      this.isRun = false;
      clearInterval(this.timerInterval);
    },
    resetTimer() {
      this.isRun = false;
      clearInterval(this.timerInterval);
      this.time = 0;
    },
  },
};
</script>

<style scoped>
.counter {
  width: 225px;
  background-color: #696969;
  margin: 22px 25px;
}

.count {
  height: 60px;
  border-bottom: 1px solid #ffffff;
  color: #9e9e9e;
  display: flex;
  justify-content: center;
  align-items: center;
}

.buttons {
  height: 60px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 0 40px;
}

.button {
  cursor: pointer;
}

.stop {
  background-color: #9e9e9e;
  height: 20px;
  width: 20px;
}

.play {
  width: 0;
  height: 0;
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
  border-left: 17px solid #9e9e9e;
}

.pause::before {
  content: "";
  position: absolute;
  left: 2px;
  background-color: #ffffff;
  height: 20px;
  width: 3px;
}
.pause::after {
  content: "";
  position: absolute;
  left: 9px;
  background-color: #ffffff;
  height: 20px;
  width: 3px;
}

.active {
  background-color: #ffffff;
}

.active_count {
  color: #ffffff;
}

.pause {
  position: relative;
  height: 20px;
  width: 17px;
}
</style>
