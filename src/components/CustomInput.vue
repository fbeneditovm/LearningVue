<template>
  <div>
    <label>
      {{ label }}
    </label>
  </div>
  <div>
    <input :type="type" v-model="inputValue" :rules="validationRules" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CustomInput",

  props: ["label", "type", "modelValue", "validationRules"],

  data() {
    return {
      title: "Login Form",
    };
  },

  //Lifecycle hooks
  //https://v3.vuejs.org/guide/composition-api-lifecycle-hooks.html#lifecycle-hooks
  created() {
    console.log(this.label + " created");
  },
  mounted() {
    console.log(this.label + " mounted");
  },
  unmounted() {
    console.log(this.label + " unmounted");
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
