<template>
  <div class="digit">
     <Clock v-for="i in 6" :key="i" :class="`digit-${num}-clock-${i - 1}`" />
  </div>
</template>

<script>
import { ref, watch } from "vue";
import Clock from "./Clock.vue";

export default {
  components: { Clock },
  name: "Digit",
  props: ["number"],
  setup(props) {
    const num = ref(props.number);

    watch(
      () => props.number,
      (first) => {
        num.value = first;
      }
    );

    return { num };
  },
};
</script>

<style lang="scss">
@import '../styles/_variables.scss';

.digit {
  display: flex;
  flex-wrap: wrap;
  width: ($clock-size * 2) + ($clock-margin * 4);

  @media screen and (max-width: 820px) {
      width: ( calc($clock-size / 2) * 2 ) + ( calc($clock-margin / 2) * 4 );
  }
}
</style>