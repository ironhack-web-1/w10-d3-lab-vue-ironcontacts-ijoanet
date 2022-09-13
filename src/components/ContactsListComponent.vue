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
      <th> Actions</th>
    </tr>
    <Contact v-for="item in list" :key="item.id" :contact="item" @deleteItem="deleteItemFromList" />
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
  methods: {
    deleteItemFromList(id) {
      this.$emit('deleteItemFromList', id);
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
