<template>
  <AddStaff @formSubmission="addValue()" />
  <v-card class="mx-auto" max-width="344">
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
      width="auto"
    ></v-img>

    <v-card-title> {{ name }}</v-card-title>

    <v-card-subtitle>{{ email }}</v-card-subtitle>

    <v-card-subtitle>{{ phone }}</v-card-subtitle>

    <v-card-subtitle>{{ gender }}</v-card-subtitle>

    <v-card-actions>
      <v-btn color="orange lighten-2" text> Edit </v-btn>
      <v-btn color="red lighten-2" text> Delete </v-btn>

      <v-spacer></v-spacer>

      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          <b>Comments/About the Staff</b> <br />
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Magni sed
          vero ratione enim? Modi laborum error, ex temporibus nesciunt
          molestiae facere voluptatibus nihil consequuntur voluptatum maxime
          perferendis reprehenderit. Earum, voluptatum!
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
import AddStaff from "./AddStaff.vue";
export default {
  data: () => ({
    show: false,
    staffs: [],
  }),
  components: { AddStaff },
  props: ["name", "email", "phone", "gender"],
  methods: {
    addValue() {
      this.$emit("formSubmitted", $event.target.value);
    },
  },
};
</script>
