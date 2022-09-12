<template>
  <tr>
    <td><img :src="contact.pictureUrl"></td>
    <td>{{ contact.name }}</td>
    <td>{{ contact.popularity.toFixed(2) }}</td>
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
    width: 6rem;
}
</style>
