<template>
  <form class="form" @submit.prevent="onSubmit(item)">
    <label>Наименование товара</label>
    <input type="text" v-model.trim="item.name" placeholder="Введите наименование товара">

    <label>Описание товара</label>
    <textarea type="text" v-model.trim="item.description" placeholder="Введите описание товара"></textarea>

    <label>Ссылка на изображение</label>
    <input type="text" v-model.trim="item.imageUrl" placeholder="Введите ссылку">

    <label>Цена товара</label>
    <input type="number" v-model.trim="item.price" placeholder="Введите цену">

    <button>Добавить товар</button>
  </form>
</template>

<script>
export default {
  name: 'AddItemForm',
  data() {
    return {
      item: {
        name: '',
        imageUrl: '',
        description: '',
        price: ''
      }
    }
  },
  methods: {
    onSubmit(item) {
      this.$emit('create-item', item);
    }
  }
}
</script>

<style>
.form {
  display: flex;
  flex-direction: column;
  width: 332px;
}
</style>