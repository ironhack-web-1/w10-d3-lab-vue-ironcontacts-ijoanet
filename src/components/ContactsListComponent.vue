<template>
  <table>
    <tr>
      <th>Picture</th>
      <th>Name</th>
      <th>Popularity</th>
      <th class="trophy">
        Won an Oscar
      </th>
      <th class="trophy">
        Won an Emmy
      </th>
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
    margin: auto;
}
th {
    font-size: 1.5rem;
}
.trophy {
    width: 10rem;
}
</style>
