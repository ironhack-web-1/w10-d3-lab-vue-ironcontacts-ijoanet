<template>
  <div class="app">
    <h1>IronContacts</h1>
    <div class="button-container">
      <button @click="addRandomContact">
        Add Random Contact
      </button>
      <button @click="sortByPopularity">
        Sort by popularity
      </button>
      <button @click="sortByName">
        Sort by name
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

// Limit contacts to 5
const currentIndex = 5;
const contacts = contactsShuffled.slice(0, currentIndex);

console.log(contactsShuffled);

export default {
  name: 'App',
  components: {
    ContactsList,
  },
  data() {
    return {
      contacts,
      contactsShuffled,
      currentIndex,
      popularityAscending: false,
      nameAscending: false,

    };
  },
  methods: {
    addRandomContact() {
      this.contacts.push(this.contactsShuffled[this.currentIndex]);
      this.currentIndex += 1;
    },
    sortByPopularity() {
      if (this.popularityAscending) {
        this.contactsShuffled.sort((prev, next) => prev.popularity - next.popularity);
      } else {
        this.contactsShuffled.sort((prev, next) => next.popularity - prev.popularity);
      }
      this.contacts = this.contactsShuffled.slice(0, this.currentIndex);
      this.popularityAscending = !this.popularityAscending;
    },
    sortByName() {
      if (this.nameAscending) {
        this.contactsShuffled.sort((prev, next) => prev.name.localeCompare(next.name));
      } else {
        this.contactsShuffled.sort((prev, next) => next.name.localeCompare(prev.name));
      }
      this.contacts = this.contactsShuffled.slice(0, this.currentIndex);
      this.nameAscending = !this.nameAscending;
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
