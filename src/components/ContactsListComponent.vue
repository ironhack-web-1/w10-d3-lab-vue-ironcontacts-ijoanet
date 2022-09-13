<template>
  <table>
    <tr>
      <th>Picture</th>
      <th>Name</th>
      <th>Popularity</th>
      <th>Won an Oscar</th>
      <th>Won an Emmy</th>
    </tr>
    <Contact v-for="item in list" :key="item.id" :contact="item" />
  </table>
</template>

<script>
import Contact from './ContactComponent.vue';

export default {
  name: 'ContactsListComponent',
  components: {
    Contact,
  },
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
table {
    width: 50rem;
    margin: auto;
}
th {
    font-size: 1.5rem;
}
</style>
