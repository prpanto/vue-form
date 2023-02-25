<script setup>
import { ref } from "vue";
import Form from "@/components/Form.vue";
import Field from "@/components/Field.vue";
import Input from "@/components/Input.vue";

const form = ref({
  name: "",
  email: "",
  password: "",
});

const errors = ref({});

function submit() {
  errors.value = {
    name: "Name is invalid because...",
    email: "Email is invalid because...",
    password: "Password is invalid because...",
  };
}
</script>

<template>
  <Form @submit.prevent="submit">
    <Field
      label="Name"
      required
      :error="errors.name"
    >
      <Input
        v-model="form.name"
        placeholder="John Doe"
        type="text"
      />
    </Field>

    <Field
      label="Email"
      required
      :error="errors.email"
    >
      <Input
        v-model="form.email"
        placeholder="john@doe.com"
        type="email"
      />
    </Field>

    <Field
      label="Password"
      required
      :error="errors.password"
      help="Should be at least 8 characters long."
    >
      <Input
        v-model="form.password"
        type="password"
      />
    </Field>

    <div class="flex justify-end">
      <button class="py-2 px-4 bg-blue-600 text-white font-medium rounded-md">Register</button>
    </div>
  </Form>
</template>
