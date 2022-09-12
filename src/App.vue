<template>
  <div class="app">
    <h1>IronContacts</h1>
    <ContactsList :list="contacts" />
  </div>
</template>

<script>
import ContactsList from './components/ContactsListComponent.vue';

import contacts from './contacts.json';

console.log(contacts);

export default {
  name: 'App',
  components: {
    ContactsList,
  },
  data() {
    return {
      contacts,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
