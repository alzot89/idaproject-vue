<template>
  <li>
    <button type="button" class="item__bin" @click="onClick">
      <img src="../assets/bin.svg" alt="картинка: корзина" class="item__bin-image">
    </button>
    <img class="item__image" :src="imageUrl" :alt="name">
    <h2 class="item__name">{{ name }}</h2>
    <p class="item__description">{{ description }}</p>
    <p>{{ `${price.toLocaleString()} руб.` }}</p>
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
li {
  position: relative;
}

.item__image {
  width: 100%;
  object-fit: contain;
}

.item__name {
  font-family: 'Source Sans Pro';
  font-weight: 600;
  font-size: 20px;
  line-height: 1.25;
}

.item__description {
  font-family: 'Source Sans Pro';
  font-weight: 600;
  font-size: 16px;
  line-height: 1.25;
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
  cursor: pointer;
}

.item__bin-image {
  width: 16px;
  height: 16px;
}
</style>