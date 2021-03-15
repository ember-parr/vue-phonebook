<template>
  <div class="mb-5">
    <h3 class="teal--text">Contacts</h3>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th>Name</th>
            <th>Phone</th>
            <th>Type</th>
            <th>Email</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="contact in contacts" :key="contact.phone">
            <td>{{ contact.firstName }} {{ contact.lastName }}</td>
            <td>{{ contact.phone }}</td>
            <td>{{ contact.type }}</td>
            <td>{{ contact.email }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  props: ["contacts"],
};
</script>

<style></style>