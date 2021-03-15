<template>
  <div>
    <h3 class="teal--text">New Contact</h3>
    <v-form @submit.prevent="handleSave" ref="contactForm">
      <v-text-field
        outlined
        label="First Name"
        v-model="form.firstName"
        :rules="validators.firstName"
      />
      <v-text-field outlined label="Last Name" v-model="form.lastName" />
      <v-text-field
        outlined
        label="Phone Number"
        v-model="form.phone"
        :rules="validators.phone"
      />
      <v-select
        outlined
        label="Phone Type"
        :items="phoneTypes"
        v-model="form.type"
      />
      <v-text-field
        outlined
        label="Email"
        v-model="form.email"
        :rules="validators.email"
      />
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
      phoneTypes: ["Home", "Mobile", "Work"],
      validators: {
        firstName: [
          val => !!val || "Contact first name is required",
          val => val.length < 25 || "First name must be less than 25 characters"
        ],
        lastName: [
          val => val.length < 25 || "Last name must be less than 25 characters"
        ],
        phone: [
          val =>
            Number.isInteger(Number(val)) || "Phone can only contain numbers"
        ],
        email: [
          val =>
            /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(val) ||
            "Invalid email address"
        ]
      }
    };
  },
  methods: {
    handleSave() {
      const isValid = this.$refs.contactForm.validate();
      if (!isValid) {
        return;
      }
      this.$emit("contact-save", this.form);
      this.form = {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: ""
      };
      this.$refs.contactForm.resetValidation();
    }
  }
};
</script>

<style scoped></style>
