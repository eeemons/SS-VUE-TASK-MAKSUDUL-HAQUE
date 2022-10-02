<template>
  <div class="black-background">
    <div class="container">
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="name"
          :counter="20"
          :rules="nameRules"
          label="Name"
          required
        ></v-text-field>

        <v-text-field
          v-model="email"
          :rules="emailRules"
          label="E-mail"
          required
        ></v-text-field>

        <v-text-field
          v-model="phone"
          :counter="11"
          :rules="phoneRules"
          label="Phone"
          required
        ></v-text-field>

        <v-select
          v-model="selectedGender"
          :items="genderItems"
          :rules="[(v) => !!v || 'Gender is required']"
          label="Gender"
          required
        ></v-select>

        <v-checkbox
          v-model="checkbox"
          :rules="[(v) => !!v || 'You must agree to continue!']"
          label="Info provided are correct"
          required
        ></v-checkbox>

        <v-btn
          :disabled="!valid"
          color="success"
          class="mr-4"
          @click="
            validate();
            onSubmit();
          "
        >
          Add Staff
        </v-btn>
        <v-btn color="error" class="mr-4" @click="reset">Reset Values </v-btn>
      </v-form>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    staff: [],

    name: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 20) || "Name must be less than 20 characters",
    ],

    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],

    phone: "",
    phoneRules: [
      (v) => !!v || "Phone is required",
      (v) => (v && v.length == 11) || "Phone must be 11 characters",
    ],

    selectedGender: null,
    genderItems: ["Male", "Female", "Other"],
    checkbox: false,
  }),

  methods: {
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
    onSubmit() {
      this.$emit("formSubmission", $event.target.value);
    },
  },
};
</script>

<style scoped>
.black-background {
  margin: 1em;
}
</style>
