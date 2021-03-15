<template>
  <div>
    <h1>Phonebook stuff goes here</h1>
    <contact-form @contact-save="saveContact" />
  </div>
</template>

<script>
import ContactForm from "./ContactForm.vue";
export default {
  data() {
    return {
      contacts: []
    };
  },
  components: { ContactForm },
  methods: {
    saveContact(contact) {
      this.contacts.push(contact);
    }
  }
};
</script>

<style scoped></style>
