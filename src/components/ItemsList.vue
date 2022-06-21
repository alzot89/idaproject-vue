<template>

  <ul>
    <ListItem v-for="(item, index) in items" :key="index" :name="item.name" :description="item.description"
      :imageUrl="item.imageUrl" :price="item.price" @delete-item="deleteItem(index)" />
  </ul>

</template>

<script>
import ListItem from '../components/Item.vue';
export default {
  name: 'ItemsList',
  props: ['items'],
  components: {
    ListItem
  },
  methods: {
    deleteItem(index) {
      this.$emit('delete-item', index)
    }
  }
}

</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(3, 332px);
  gap: 16px;
}
</style>