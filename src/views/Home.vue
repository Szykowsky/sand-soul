<template>
  <div class="home">
    <div>
      <neon-paragraph>Some random text</neon-paragraph>
    </div>
    <div>
      <primary-button>Test button</primary-button>
    </div>
    <div>
      <primary-button :isLoading="true"></primary-button>
    </div>
    <div>
      <primary-button :disabled="true">Disabled</primary-button>
    </div>
    <div>
      <neon-paragraph :style="'flicker'">
        Some random flicker text
      </neon-paragraph>
    </div>
    <div>
      <custom-input>First Name</custom-input>
    </div>
    <div>
      <custom-input>Last Name</custom-input>
    </div>
    <div>
      <custom-input>Email </custom-input>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import PrimaryButton from "@/components/buttons/PrimaryButton.vue";
import NeonParagraph from "@/components/typography/NeonParagraph.vue";
import CustomInput from "@/components/controls/CustomInput.vue";

export default defineComponent({
  name: "Home",
  components: {
    PrimaryButton,
    NeonParagraph,
    CustomInput,
  },
});
</script>
<style scoped>
.home {
  margin-top: 24px;
}
</style>
