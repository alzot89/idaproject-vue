<template>

  <ul class="items-list">
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
.items-list {
  max-width: 75%;
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 16px;
}

@media screen and (max-width: 710px) {
  .items-list {
    margin: 16px auto 0;
  }
}
</style>