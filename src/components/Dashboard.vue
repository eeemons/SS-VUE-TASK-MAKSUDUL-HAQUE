<template>
  <div class="container">
    <h1>Welcome to the dashboard</h1>
    <v-btn color="green lighten-2" text @click="toggleVisibility()">
      Add
    </v-btn>
    <AddStaff v-show="visible" />

    <Staff
      :name="this.name"
      :email="this.email"
      :phone="this.phone"
      :gender="this.gender"
      @formSubmitted="addValue()"
    />
    <router-link to="/">Home</router-link>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Staff from "./Staff.vue";
import AddStaff from "./AddStaff.vue";

let name = "Default",
  email = "default@email.com",
  phone = "01234567890",
  gender = "N/A",
  visible = ref(false);

function toggleVisibility() {
  visible.value = !visible.value;
  console.log(visible);
}
function addValue($event) {
  console.log($event);
}
</script>

<style scoped>
* {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
