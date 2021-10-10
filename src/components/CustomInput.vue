<template>
  <div>
    <label>
      {{ label }}
    </label>
  </div>
  <div>
    <input :type="type" v-model="inputValue" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CustomInput",

  props: ["label", "type", "modelValue"],

  data() {
    return {
      title: "Login Form",
    };
  },

  computed: {
    inputValue: {
      get(): string {
        return this.modelValue;
      },
      set(newValue: string) {
        this.$emit("update:modelValue", newValue);
      },
    },
  },
});
</script>

<style scoped></style>
