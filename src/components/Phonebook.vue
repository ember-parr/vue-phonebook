<template>
  <div>
    <h1>Phonebook stuff goes here</h1>
    <v-row>
      <v-col :lg="8" :sm="12">
        <contacts-table :contacts="contacts" />
      </v-col>
      <v-col :lg="4" :sm="12">
        <contact-form @contact-save="saveContact" />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ContactForm from "./ContactForm.vue";
import ContactsTable from "./ContactsTable";
export default {
  data() {
    return {
      contacts: []
    };
  },
  mounted() {
    const existingContacts = JSON.parse(localStorage.getItem("contacts"));
    this.contacts = existingContacts || [];
  },
  components: { ContactForm, ContactsTable },
  methods: {
    saveContact(contact) {
      this.contacts.push(contact);
      localStorage.setItem("contacts", JSON.stringify(this.contacts));
    }
  }
};
</script>

<style scoped></style>
