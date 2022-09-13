<template>
  <tr>
    <td><img :src="contact.pictureUrl"></td>
    <td>{{ contact.name }}</td>
    <td>{{ contact.popularity.toFixed(2) }}</td>
    <td><span v-if="contact.wonOscar" class="trophy">🏆</span></td>
    <td><span v-if="contact.wonEmmy" class="trophy">🏆</span></td>
  </tr>
</template>

<script>
export default {
  name: 'ContactComponent',
  props: {
    contact: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
img {
    width: 5.5rem;
}
.trophy {
    font-size: 2rem;
}
</style>
