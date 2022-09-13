<template>
  <div class="app">
    <h1>IronContacts</h1>
    <div class="button-container">
      <button @click="addRandomContact">
        Add Random Contact
      </button>
    </div>
    <ContactsList :list="contacts" />
  </div>
</template>

<script>
import ContactsList from './components/ContactsListComponent.vue';

import contactsRaw from './contacts.json';

const contactsShuffled = contactsRaw.map((value) => ({ value, sort: Math.random() }))
  .sort((a, b) => a.sort - b.sort)
  .map(({ value }) => value);

console.log(contactsRaw);

// Limit contacts to 5
const currentIndex = 5;
const contacts = contactsShuffled.splice(0, currentIndex);

export default {
  name: 'App',
  components: {
    ContactsList,
  },
  data() {
    return {
      contacts,
      contactsShuffled,
      currentIndex: 5,
    };
  },
  methods: {
    addRandomContact() {
      this.contacts.push(this.contactsShuffled[this.currentIndex]);
      this.currentIndex += 1;
    },
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
.button-container {
    margin-bottom: 20px;
}
button {
    font-size: 1rem;
}
</style>
