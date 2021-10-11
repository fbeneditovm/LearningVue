<template>
  <form @submit.prevent="handleSubmit()">
    <h1>{{ title }}</h1>
    <div>
      <label>Server number</label>
    </div>
    <div>
      <!-- v-model.number ensures a number value -->
      <input type="number" v-model.number="serverNumber" />
    </div>
    <div v-for="(input, i) in inputs" :key="i" class="login-fields">
      <CustomInput
        v-model="input.value"
        :label="input.label"
        :type="input.type"
        :validation-rules="input.rules"
      />
    </div>

    <div v-if="displayConfirmation" class="login-fields">
      <CustomInput
        v-model="passwordConfirmation"
        label="Confirm Password"
        type="password"
        validation-rules="[(v) => v === inputs[1].value || 'Passwords don\'t match']"
      />
    </div>
    <button>Log in</button>
  </form>
  <div>
    <button @click="displayConfirmation = !displayConfirmation">
      Confirm password
    </button>
  </div>
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
      displayConfirmation: false,
      passwordConfirmation: "",
      serverNumber: null,
      inputs: [
        {
          label: "Email",
          value: "",
          type: "email",
          rules: [],
        },
        {
          label: "Password",
          value: "",
          type: "password",
          rules: [(v) => v.length > 5 || "Password too short"],
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
          '", Server Number=' +
          this.serverNumber +
          '"}'
      );
    },
  },
});
</script>

<style scoped></style>
