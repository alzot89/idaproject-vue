<template>
  <div class="app">
    <div class="app__container">
      <h1 class="app__title">Добавление товара</h1>
      <ItemSorter @sorting="sorting" />
    </div>
    <div class="content">
      <AddItemForm @create-item="createItem" />
      <ItemsList v-bind:items="items" @delete-item="deleteItem" />
    </div>
  </div>
</template>

<script>
import ItemsList from './components/ItemsList.vue';
import AddItemForm from './components/AddItemForm.vue';
import ItemSorter from './components/ItemSorter.vue';

export default {
  name: 'App',
  data() {
    return {
      items: [
        {
          name: 'Торшер',
          imageUrl: 'https://hoff.ru/upload/iblock/9ac/9ac76c0139edb6c955b2f08f05f9189c.jpg',
          description: 'Неплохой такой торшер, черный и светит неплохо',
          price: 21000
        },
        {
          name: 'Стул',
          imageUrl: 'https://hoff.ru/upload/iblock/249/24966ede35cdcbdef0e3e5fd80314a27.jpg',
          description: 'Зеленый такой стул из пластика на деревянных ножках',
          price: 12000
        },
        {
          name: 'Корзина',
          imageUrl: 'https://hoff.ru/upload/iblock/0ee/0ee7f8c5aabf8e69939d222244ae8e02.jpg',
          description: 'Прочная корзина для мусора из черной металлической сетки',
          price: 8000
        },
        {
          name: 'Торшер',
          imageUrl: 'https://hoff.ru/upload/iblock/9ac/9ac76c0139edb6c955b2f08f05f9189c.jpg',
          description: 'Неплохой такой торшер, черный и светит неплохо',
          price: 21000
        },
        {
          name: 'Стул',
          imageUrl: 'https://hoff.ru/upload/iblock/249/24966ede35cdcbdef0e3e5fd80314a27.jpg',
          description: 'Зеленый такой стул из пластика на деревянных ножках',
          price: 12000
        },
        {
          name: 'Корзина',
          imageUrl: 'https://hoff.ru/upload/iblock/0ee/0ee7f8c5aabf8e69939d222244ae8e02.jpg',
          description: 'Прочная корзина для мусора из черной металлической сетки',
          price: 8000
        },
        {
          name: 'Торшер',
          imageUrl: 'https://hoff.ru/upload/iblock/9ac/9ac76c0139edb6c955b2f08f05f9189c.jpg',
          description: 'Неплохой такой торшер, черный и светит неплохо',
          price: 21000
        },
        {
          name: 'Стул',
          imageUrl: 'https://hoff.ru/upload/iblock/249/24966ede35cdcbdef0e3e5fd80314a27.jpg',
          description: 'Зеленый такой стул из пластика на деревянных ножках',
          price: 12000
        },
        {
          name: 'Корзина',
          imageUrl: 'https://hoff.ru/upload/iblock/0ee/0ee7f8c5aabf8e69939d222244ae8e02.jpg',
          description: 'Прочная корзина для мусора из черной металлической сетки',
          price: 8000
        }
      ]
    }
  },
  mounted() {
    if (localStorage.getItem('items')) {
      try {
        this.items = JSON.parse(localStorage.getItem('items'));
      } catch (e) {
        localStorage.removeItem('items');
      }
    }
  },
  components: {
    ItemsList,
    AddItemForm,
    ItemSorter
  },
  methods: {
    createItem(item) {
      this.items.push({ ...item });
      this.saveItems();
    },
    deleteItem(index) {
      this.items.splice(index, 1);
      this.saveItems();
    },
    sorting(option) {
      switch (option) {
        case 'name': this.items.sort((a, b) => {
          return a.name.localeCompare(b.name);
        })
          break
        case 'min': this.items.sort((a, b) => {
          return a.price - b.price;
        })
          break
        case 'max': this.items.sort((a, b) => {
          return b.price - a.price;
        })
          break
        default: this.items.sort();
      }
    },
    saveItems() {
      const parsed = JSON.stringify(this.items);
      localStorage.setItem('items', parsed);
    }
  }
}
</script>

<style>
@import url('./fonts/fonts.css');

body {
  margin: 0;
}

.app {
  font-family: 'Source Sans Pro', 'Inter', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  max-width: 1440px;
  margin: 0 auto;
  background-color: #FFFEFB;
  display: flex;
  flex-direction: column;
  padding: 32px;
  box-sizing: border-box;
}

.app__container {
  display: flex;
  flex-wrap: wrap;
}

.app__title {
  font-family: 'Source Sans Pro';
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
  color: #3F3F3F;
}

.content {
  display: flex;
  margin-top: 16px;
  align-items: flex-start;
  position: relative;
}

@media screen and (max-width: 710px) {
  .app {
    padding: 16px;
  }

  .app__container {
    flex-direction: column;
  }

  .content {
    flex-direction: column;
  }
}

h1,
h2,
h3 {
  margin: 0;
}

p {
  margin: 0;
}

button {
  cursor: pointer;
  transition: .4s opacity ease;
}

button:hover {
  opacity: .6;
}
</style>
