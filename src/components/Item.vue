<template>
  <li class="item">
    <button type="button" class="item__bin" @click="onClick">
      <img src="../assets/bin.svg" alt="картинка: корзина" class="item__bin-image">
    </button>
    <img class="item__image" :src="imageUrl" :alt="name">
    <div class="item__container">
      <h2 class="item__name">{{ name }}</h2>
      <p class="item__description">{{ description }}</p>
      <p class="item__price">{{ `${price.toLocaleString()} руб.` }}</p>
    </div>
  </li>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    name: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: false
    },
    imageUrl: {
      type: String,
      required: true
    },
    price: {
      type: Number,
      required: true
    }
  },
  methods: {
    onClick() {
      this.$emit('delete-item');
    }
  }
}

</script>

<style>
.item {
  position: relative;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}

.item__image {
  width: 100%;
  object-fit: contain;
  border-top-left-radius: 4px;
  border-top-right-radius: 4px;
}

.item__container {
  padding: 16px 16px 24px;
}

.item__name {
  font-family: 'Source Sans Pro';
  font-weight: 600;
  font-size: 20px;
  line-height: 1.25;
}

.item__description {
  margin-top: 16px;
  font-family: 'Source Sans Pro';
  font-weight: 600;
  font-size: 16px;
  line-height: 1.25;
}

.item__price {
  margin-top: 32px;
  font-family: 'Source Sans Pro';
  font-weight: 600;
  font-size: 24px;
  line-height: 30px;
  color: #3F3F3F;
}

.item__bin {
  padding: 8px;
  border: none;
  width: 32px;
  height: 32px;
  border-radius: 10px;
  background-color: #FF8484;
  position: absolute;
  top: -4px;
  right: -4px;
}

.item__bin-image {
  width: 16px;
  height: 16px;
}
</style>