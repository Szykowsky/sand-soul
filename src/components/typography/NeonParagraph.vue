<template>
  <p class="text" :class="getStyle">
    <slot />
  </p>
</template>
<script lang="ts">
import { computed, defineComponent } from "vue";

export default defineComponent({
  props: {
    style: String,
  },
  setup(props) {
    const getStyle = computed(() => {
      switch (props.style) {
        case "flicker":
          return "neon-text-flicker";
        default:
          return "neon-text";
      }
    });

    return {
      getStyle,
    };
  },
});
</script>
<style lang="scss" scoped>
@import '@/scss/animations.scss';

p {
    margin: 24px;
}

.text {
  font-size: 18px;
}

.neon-text {
  color: $primary-color;
  text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px $text-shadow-color,
    0 0 82px $text-shadow-color, 0 0 92px $text-shadow-color, 0 0 102px $text-shadow-color, 0 0 151px $text-shadow-color;
}

.neon-text-flicker {
  color: $primary-color;
  animation: flicker 1.5s infinite alternate;
}
</style>