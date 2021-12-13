<template>
  <div class="container" @mousemove="mousemove">
    <div class="clock-wrap" v-if="timeParts">
      <div class="clock-wrap-group">
        <Digit :number="timeParts[0][0]" />
        <Digit :number="timeParts[0][1]" />
      </div>
      <div class="clock-wrap-group">
        <Digit :number="timeParts[1][0]" />
        <Digit :number="timeParts[1][1]" />
      </div>
      <div class="clock-wrap-group">
        <Digit :number="timeParts[2][0]" />
        <Digit :number="timeParts[2][1]" />
      </div>
    </div>
    <div class="modes" :class="{ 'is-active': showModesButton }">
      <button @click="darkMode = !darkMode">
        <span v-if="darkMode" class="material-icons material-icons-sharp"
          >light_mode</span
        >
        <span v-else class="material-icons material-icons-sharp"
          >dark_mode</span
        >
      </button>
      <button @click="fullScreen = !fullScreen">
        <span v-if="fullScreen" class="material-icons material-icons-sharp"
          >fullscreen_exit</span
        >
        <span v-else class="material-icons material-icons-sharp"
          >fullscreen</span
        >
      </button>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import { watch } from "@vue/runtime-core";
import Digit from "./components/Digit.vue";

export default {
  name: "App",
  components: { Digit },
  setup() {
    const darkMode = ref(false);
    const showModesButton = ref(false);
    const fullScreen = ref(false);

    const timeParts = ref([
      ["placeholder", "placeholder"],
      ["placeholder", "placeholder"],
      ["placeholder", "placeholder"],
    ]);

    setTimeout(() => {
      startClock();
    }, 1000);

    const startClock = () => {
      setInterval(function () {
        const date = new Date();
        timeParts.value = [
          date.getHours(),
          date.getMinutes(),
          date.getSeconds(),
        ].map((n) => {
          return ("0" + n).slice(-2).split("");
        });
      }, 1000);
    };

    watch(
      () => darkMode.value,
      (val) => {
        if (val) {
          document.body.classList.add("dark-mode");
        } else {
          document.body.classList.remove("dark-mode");
        }
      }
    );

    watch(
      () => fullScreen.value,
      (val) => {
        if (val) {
          openFullscreen(document.documentElement);
        } else {
          closeFullscreen();
        }
      }
    );

    darkMode.value = window.matchMedia("(prefers-color-scheme: dark)").matches;

    const openFullscreen = (elem) => {
      if (elem.requestFullscreen) {
        elem.requestFullscreen();
      } else if (elem.webkitRequestFullscreen) {
        elem.webkitRequestFullscreen();
      } else if (elem.msRequestFullscreen) {
        elem.msRequestFullscreen();
      }
    };

    const closeFullscreen = () => {
      if (document.exitFullscreen) {
        document.exitFullscreen();
      } else if (document.webkitExitFullscreen) {
        document.webkitExitFullscreen();
      } else if (document.msExitFullscreen) {
        document.msExitFullscreen();
      }
    };

    let cursorTimeout = null;
    const mousemove = () => {

      if (!showModesButton.value) {
        showModesButton.value = true;
        setTimeout(function () {
          showModesButton.value = false;
        }, 2000);
      }
      
      document.body.style.cursor = 'default';
      clearTimeout(cursorTimeout);
      cursorTimeout = setTimeout(() => {
        if(fullScreen.value) {
          document.body.style.cursor = 'none'
        }
      }, 2000);
      
    };

    return { timeParts, darkMode, mousemove, showModesButton, fullScreen };
  },
};
</script>

<style lang="scss">
@import "styles/_variables.scss";

* {
  box-sizing: border-box;
}

html,
body,
#app,
.container {
  height: 100%;
}

body {
  background: $white-bg;
  position: relative;
  margin: 0;

  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: $dark-bg;
    opacity: 0;
    pointer-events: none;
  }

  &.dark-mode {
    &::after {
      opacity: 1;
    }
  }
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 1;
}

.modes {
  margin-top: 30px;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s;

  button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: none;
    margin: 0 10px;
    background: rgba(0, 0, 0, 0.1);
    color: #fff;
    outline: none;
    cursor: pointer;
    transition: all 0.1s;

    &:hover {
      background: rgba(0, 0, 0, 0.2);
    }
  }

  &:hover,
  &.is-active {
    opacity: 0.5;
    visibility: visible;
    transition: opacity 1s;
  }

  &:hover {
    opacity: 1;
  }
}

.clock-wrap {
  display: flex;
  padding: $container-padding;
  background: $white-bg;
  box-shadow: -1px 4px 20px 2px rgba(0, 0, 0, 0.05);
  border-radius: 10px;
  margin-left: -#{$digit-group-indent};
  margin-right: -#{$digit-group-indent};

  @media screen and (max-width: 820px) {
    padding: $container-padding / 2;
	margin-left: -#{$digit-group-indent / 2};
    margin-right: -#{$digit-group-indent / 2};
  }

  .dark-mode & {
    background-color: $dark-bg;
    box-shadow: unset;
  }

  &-group {
    display: flex;
    margin-left: $digit-group-indent;
    margin-right: $digit-group-indent;

	@media screen and (max-width: 820px) {
		margin-left: $digit-group-indent / 2;
        margin-right: $digit-group-indent / 2;
	}
  }
}
</style>
