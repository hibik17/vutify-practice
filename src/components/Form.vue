<template>
  <v-form ref="form" lazy-validation>
    <!-- user name form -->
    <v-text-field
      v-model="userData.name"
      :counter="10"
      label="Name"
      :rules="nameRules"
      required
    ></v-text-field>
    <!-- user email form -->
    <v-text-field
      label="Email"
      v-model="userData.email"
      required
      :rules="emailRules"
    ></v-text-field>
    <!-- user gender form -->
    <v-select
      v-model="userData.gender"
      label="Gender"
      :items="gender"
      :rules="[(v) => !!v || 'Gender is required']"
      transition="slide-x-transition"
      required
    ></v-select>
    <!-- submit button -->
    <v-btn color="success" @click="formSubmit" class="text-center text-center">
      Sign up
    </v-btn>
  </v-form>
</template>

<script setup lang="ts">
import { reactive } from "vue";

type userType = {
  name: string;
  email: string;
  gender: string;
};

const userData: userType = reactive({
  name: "",
  email: "",
  gender: "",
});

const nameRules: any = [
  (v) => !!v || "Name is required",
  (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
];

const emailRules: any = [
  (v) => !!v || "Email is required",
  (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
];

const gender: Array<string> = ["man", "woman", "others"];

const formSubmit = () => {
  alert("submit");
};
</script>
