<template>
  <div class="question">
    <input type="text" required />
    <label><slot/></label>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
// import { useInputValidator } from "@/helpers/useInputValidator";
export default defineComponent({
  name: "CustomInput",
  props: {
    value: String,
    label: String,
    type: String,
  },
  //   setup(props, { emit }) {
  //     const { input, errors } = useInputValidator(
  //       props.value,
  //       [],
  //       (value: string) => emit("update:modelValue", value)
  //     );
  //     return {
  //       input,
  //       errors,
  //     };
  //   },
});
</script>
<style lang="scss" scoped>
@import '@/scss/animations.scss';

.transition {
  @include transition(all 0.25s cubic-bezier(0.53, 0.01, 0.35, 1.5));
}

.question {
  position: relative;
  padding: 24px 0;
}

label {
  @extend .transition;
  transform-origin: left center;
  color: $primary-color;
  font-weight: 100;
  letter-spacing: 0.01em;
  font-size: 18px;
  box-sizing: border-box;
  padding: 8px 15px;
  display: block;
  position: absolute;
  margin-top: -40px;
  z-index: 2;
  pointer-events: none;
}

input[type="text"] {
  @extend .transition;
  appearance: none;
  background-color: transparent;
  border: 2px solid $primary-color;
  line-height: 0;
  font-size: 18px;
  width: 100%;
  display: block;
  box-sizing: border-box;
  padding: 10px 15px;
  color: $primary-color;
  font-weight: 100;
  letter-spacing: 0.01em;
  position: relative;
  z-index: 1;

  &:focus {
    outline: none;
    background: $primary-color;
    color: white;
    margin-top: 30px;
    box-shadow: 0 0 4px 2px #fff, 0 0 7px #fff, 0 0 12px #fff,
      0 0 18px $text-shadow-color, 0 0 32px $text-shadow-color,
      0 0 44px $text-shadow-color;
  }

  &:valid {
    margin-top: 30px;
  }

  &:focus ~ label {
    @include translate(0, -45px);
  }

  &:valid ~ label {
    text-transform: uppercase;
    font-style: italic;
    @include transform(translate(5px, -45px) scale(0.6));
  }
}
</style>