<template>
  <div class="content">
    <AddItemForm @create-item="createItem" />
    <ItemsList v-bind:items="items" />
  </div>
</template>

<script>
import ItemsList from './components/ItemsList.vue';
import AddItemForm from './components/AddItemForm.vue';

export default {
  name: 'App',
  data() {
    return {
      items: [
        { name: 'Торшер с выключателем TL-510B', imageUrl: 'https://hoff.ru/upload/iblock/9ac/9ac76c0139edb6c955b2f08f05f9189c.jpg', description: 'Неплохой такой торшер, черный и светит неплохо', price: 21000 },
        { name: 'Стул Aspen', imageUrl: 'https://hoff.ru/upload/iblock/249/24966ede35cdcbdef0e3e5fd80314a27.jpg', description: 'Зеленый такой стул из пластика на деревянных ножках', price: 12000 },
        { name: 'Корзина для мусора MITTE Roca 12 л', imageUrl: 'https://hoff.ru/upload/iblock/0ee/0ee7f8c5aabf8e69939d222244ae8e02.jpg', description: 'Прочная и при этом стильная корзина для мусора Roca выполнена из черной металлической сетки и имеет особую устойчивость благодаря цельнометаллическому дну', price: 8000 }
      ]
    }
  },
  components: {
    ItemsList,
    AddItemForm
  },
  methods: {
    createItem(item) {
      this.items.push(item)
    }
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
  display: flex;
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
