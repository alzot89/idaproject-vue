<template>

  <ul>
    <Item v-for="(item, index) in items" :key="index" :name="item.name" :description="item.description"
      :imageUrl="item.imageUrl" :price="item.price" />
  </ul>

</template>

<script>
import Item from '../components/Item.vue';
export default {
  name: 'ItemsList',
  props: ['items'],
  components: {
    Item
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