<template>
  <form @submit.prevent="handleSubmit()">
    <h1>{{ title }}</h1>
    <div class="login-fields">
      <CustomInput v-model="form.email" :label="emailLabel" />
    </div>
    <div class="login-fields">
      <CustomInput v-model="form.password" :label="passwordLabel" />
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
      emailLabel: "Email",
      passwordLabel: "Password",
      form: {
        email: "",
        password: "Use letters and numbers",
      },
    };
  },

  methods: {
    handleSubmit(): void {
      console.log(
        'Submitted {Email="' +
          this.form.email +
          '", Password="' +
          this.form.password +
          '"}'
      );
    },
  },
});
</script>

<style scoped></style>
