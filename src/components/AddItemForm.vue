<template>
  <form class="form" @submit.prevent="onSubmit(item)">
    <label class="form__label form__label_mandatory">Наименование товара</label>
    <input class="form__input" type="text" v-model.trim="item.name" placeholder="Введите наименование товара">
    <p v-show="error.name">Поле является обязательным</p>

    <label class="form__label">Описание товара</label>
    <textarea class="form__input" type="text" v-model.trim="item.description"
      placeholder="Введите описание товара"></textarea>

    <label class="form__label form__label_mandatory">Ссылка на изображение</label>
    <input class="form__input" type="text" v-model.trim="item.imageUrl" placeholder="Введите ссылку">
    <p v-show="error.imageUrl">Поле является обязательным</p>

    <label class="form__label form__label_mandatory">Цена товара</label>
    <input class="form__input" type="number" v-model.trim="item.price" placeholder="Введите цену">
    <p v-show="error.price">Поле является обязательным</p>

    <button class="form__button" :class="{ 'form__button_disabled': !isFormValid }">Добавить товар</button>
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
      },
      error: {
        name: false,
        imageUrl: false,
        price: false
      }
    }
  },
  methods: {
    onSubmit(item) {
      console.log(123);
      this.validator();
      if (!this.isFormValid) {
        return;
      }
      this.$emit('create-item', item);
      this.formReset();
    },
    formReset() {
      this.item.name = '',
        this.item.imageUrl = '',
        this.item.description = '',
        this.item.price = ''
    },
    validator() {
      if (!this.item.name) {
        this.error.name = true;
      }
      if (!this.item.imageUrl) {
        this.error.name = true;
      }
      if (!this.item.price) {
        this.error.name = true;
      }
    }
  },
  computed: {
    isFormValid: function () {
      if (this.item.name && this.item.imageUrl && this.item.price) {
        return true;
      } else {
        return false;
      }
    }
  }

}
</script>

<style>
.form {
  padding: 24px;
  display: flex;
  flex-direction: column;
  width: 332px;
}

.form__label_mandatory {
  position: relative;
}

.form__label_mandatory::after {
  content: "";
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background-color: #FF8484;
  display: inline-block;
  position: absolute;
}

.form__button {
  color: #fff;
  background-color: #7BAE73;
  height: 36px;
  border: none;
  border-radius: 10px;
}

.form__button_disabled {
  color: #B4B4B4;
  background-color: #EEEEEE;
}
</style>