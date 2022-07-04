<template>
  <div class="clock">
    <div class="arrow arrow-1"></div>
    <div class="arrow arrow-2"></div>
  </div>
</template>

<style lang="scss">
@import "../styles/_variables.scss";

.clock {
  width: $clock-size;
  height: $clock-size;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  background-color: $white-bg;
  margin: $clock-margin;
  overflow: hidden;
  box-shadow: inset 2px 2px 4px 0 rgb(0 0 0 / 8%), 
              inset -7px -7px 2px -8px hsl(0deg 0% 100% / 50%), 
              -5px -5px 12px -10px rgb(242 240 246 / 70%), 
              4px 7px 11px 0 rgb(0 0 0 / 2%);

  @media screen and (max-width: 820px) {
    width: calc($clock-size / 2);
    height: calc($clock-size / 2);
    margin: calc($clock-margin / 2);
  }

  &::after {
    content: "";
    width: $arrow-height;
    height: $arrow-height;
    background: $arrow-color;
    border-radius: 50%;

    @media screen and (max-width: 820px) {
      display: none;
    }

    .dark-mode & {
      background: #c9c9c9;
    }
  }

  .dark-mode & {
    background-color: $dark-bg;
    box-shadow: unset;
  }
}

.arrow {
  width: calc(50% - 2px);
  height: $arrow-height;
  background: $arrow-color;
  position: absolute;
  transform: translateX(-50%);
  transform-origin: right center;
  transition: all 0.7s linear, opacity 0.2s, background-color 0s;
  will-change: transform;
  backface-visibility: hidden;
  z-index: 1;

  @media screen and (max-width: 820px) {
    height: floor( calc($arrow-height / 2) );
  }

  .dark-mode & {
    background: #c9c9c9;
    box-shadow: unset;
  }
}

[class*="digit-placeholder"] {
  div:first-child {
    transform: translateX(-50%) rotate(-50deg);
  }
  div:last-child {
    transform: translateX(-50%) rotate(310deg);
  }
}

.digit-1-clock-0,
.digit-1-clock-2,
.digit-1-clock-4,
.digit-4-clock-4,
.digit-7-clock-2,
.digit-7-clock-4 {
  .arrow {
    &.arrow-1, &.arrow-2 {
      transform: translateX(-50%) rotate(310deg);
    }
  }
  &::after {
    .dark-mode & {
      opacity: 0;
    }
  }
}

.digit-0 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(360deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-1 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(270deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-2 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(0);
    }
  }
}

.digit-3 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-4 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(270deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(270deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-5 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(360deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(360deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-6 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(360deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(360deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-7 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(360deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-8 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(360deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}

.digit-9 {
  &-clock-0 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-1 {
    .arrow-1 {
      transform: translateX(-50%) rotate(360deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-2 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-3 {
    .arrow-1 {
      transform: translateX(-50%) rotate(90deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(270deg);
    }
  }
  &-clock-4 {
    .arrow-1 {
      transform: translateX(-50%) rotate(180deg);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(180deg);
    }
  }
  &-clock-5 {
    .arrow-1 {
      transform: translateX(-50%) rotate(0);
    }
    .arrow-2 {
      transform: translateX(-50%) rotate(90deg);
    }
  }
}
</style>