<template>
  <button class="inner-height-neon" :disabled="disabled">
    <span class="bg-height"></span>
    <span v-if="!isLoading" class="btn-text">
      <slot />
    </span>
    <loading v-else> </loading>
  </button>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import Loading from "@/components/ui/Loading.vue";

export default defineComponent({
  name: "PrimaryBytton",
  components: {
    Loading,
  },
  props: {
    isLoading: Boolean,
    disabled: Boolean,
  },
  // setup(prop, { emit }) {},
});
</script>
<style lang="scss" scoped>

button {
  font-size: 20px;
  min-width: 230px;
  min-height: 80px;
  border-radius: 4px;
  cursor: pointer;
  margin: 24px;
}
.inner-height-neon {
  background-color: transparent;
  border: 2px solid $primary-color;
  color: $primary-color;
  -webkit-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
  position: relative;

  &:hover:enabled {
    -webkit-box-shadow: 0px 0px 30px 20px $primary-color;
    box-shadow: 0px 0px 30px 20px $primary-color;
    border-color: #6bfff1;

    .bg-height {
      height: 100%;
      top: 0%;
      z-index: -1;
    }

    .btn-text {
      color: #1aa99b;
    }
  }

  &:disabled {
    z-index: 3;
    border-color: $disabled-color;
    color: $disabled-color;
    cursor: not-allowed;
  }

  .bg-height {
    background-color: $primary-color;
    position: absolute;
    left: 0;
    right: 0;
    top: 50%;
    bottom: 0;
    height: 0%;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -webkit-transition: height 0.3s, top 0.3s;
    transition: height 0.3s, top 0.3s;
  }

  .btn-text {
    z-index: 1;
  }
}
</style>