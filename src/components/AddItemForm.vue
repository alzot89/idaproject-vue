<template>
  <form class="form" @submit.prevent="onSubmit(item)">
    <label class="form__label form__label_mandatory">Наименование товара</label>
    <input class="form__input" :class="{ 'form__input_mandatory': error.name }" type="text" v-model.trim="item.name"
      placeholder="Введите наименование товара">
    <p v-show="error.name" class="form__error">Поле является обязательным</p>

    <label class="form__label">Описание товара</label>
    <textarea class="form__input form__input_description" type="text" v-model.trim="item.description"
      placeholder="Введите описание товара"></textarea>

    <label class="form__label form__label_mandatory">Ссылка на изображение</label>
    <input class="form__input" :class="{ 'form__input_mandatory': error.imageUrl }" type="text"
      v-model.trim="item.imageUrl" placeholder="Введите ссылку">
    <p v-show="error.imageUrl" class="form__error">Поле является обязательным</p>

    <label class="form__label form__label_mandatory">Цена товара</label>
    <input class="form__input" :class="{ 'form__input_mandatory': error.price }" type="number" v-model.trim="item.price"
      placeholder="Введите цену">
    <p v-show="error.price" class="form__error">Поле является обязательным</p>

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
        this.item.price = '',
        this.error.name = false,
        this.error.imageUrl = false,
        this.error.price = false
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
  box-sizing: border-box;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}

.form__input {
  width: 100%;
  border: none;
  outline-style: none;
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  margin-top: 4px;
  padding: 10px 0 11px 16px;
  box-sizing: border-box;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type='number'] {
  -moz-appearance: textfield;
}

.form__input_description {
  height: 108px;
}

.form__input::placeholder {
  font-family: 'Source Sans Pro';
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
}

.form__input_mandatory {
  border: 1px solid #FF8484;
}

.form__label {
  font-family: 'Source Sans Pro';
  font-weight: 400;
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  color: #49485E;
  margin-top: 16px;
}

.form__label:first-of-type {
  margin: 0;
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

.form__error {
  font-family: 'Source Sans Pro';
  font-weight: 400;
  font-size: 8px;
  line-height: 10px;
  letter-spacing: -0.02em;
  color: #FF8484;
}

.form__button {
  width: 100%;
  padding: 0;
  color: #fff;
  background-color: #7BAE73;
  height: 36px;
  border: none;
  border-radius: 10px;
  margin-top: 24px;
  font-family: 'Inter';
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  letter-spacing: -0.02em;
}

.form__button_disabled {
  color: #B4B4B4;
  background-color: #EEEEEE;
}
</style>