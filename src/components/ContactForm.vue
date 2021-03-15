<template>
  <div>
    <h3 class="teal--text">New Contact</h3>
    <v-form @submit.prevent="handleSave">
      <v-text-field outlined label="First Name" v-model="form.firstName" />
      <v-text-field outlined label="Last Name" v-model="form.lastName" />
      <v-text-field outlined label="Phone Number" v-model="form.phone" />
      <v-select
        outlined
        label="Phone Type"
        :items="phoneTypes"
        v-model="form.type"
      />
      <v-text-field outlined label="Email" v-model="form.email" />
      <v-btn type="submit" color="teal" dark>Save</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: ""
      },
      phoneTypes: ["Home", "Mobile", "Work"]
    };
  },
  methods: {
    handleSave() {
      this.$emit("contact-save", this.form);
      this.form = {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: ""
      };
    }
  }
};
</script>

<style scoped></style>
