<template>
  <form @submit.prevent="handleSubmit()">
    <h1>{{ title }}</h1>
    <div v-for="(input, i) in inputs" :key="i" class="login-fields">
      <CustomInput
        v-model="input.value"
        :label="input.label"
        :type="input.type"
      />
    </div>
    <button>Log in</button>
  </form>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CustomInput from "@/components/CustomInput.vue";

export default defineComponent({
  name: "LoginComponent",
  components: {
    CustomInput,
  },
  data() {
    return {
      title: "Login Form",
      inputs: [
        {
          label: "Email",
          value: "",
          type: "email",
        },
        {
          label: "Password",
          value: "",
          type: "password",
        },
      ],
    };
  },

  methods: {
    handleSubmit(): void {
      console.log(
        'Submitted {Email="' +
          this.inputs[0].value +
          '", Password="' +
          this.inputs[1].value +
          '"}'
      );
    },
  },
});
</script>

<style scoped></style>
