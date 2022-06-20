<template>
  <div class="content">
    <ItemsList v-bind:items="items" />
  </div>
</template>

<script>
import ItemsList from './components/ItemsList.vue';

export default {
  name: 'App',
  data() {
    return {
      items: [
        { title: 'Наименование товара', description: 'Довольно таки интересное описание товара в несколько строк', price: 10000 },
        { title: 'Наименование товара', description: 'Довольно таки интересное описание товара в несколько строк', price: 12000 },
        { title: 'Наименование товара', description: 'Довольно таки интересное описание товара в несколько строк', price: 8000 }
      ]
    }
  },
  components: {
    ItemsList
  }
}
</script>

<style>
@import url('./fonts/fonts.css');

.content {
  font-family: 'Source Sans Pro', 'Inter', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  background-color: #FFFEFB;
}

h1,
h2,
h3 {
  margin: 0;
}

p {
  margin: 0;
}
</style>
