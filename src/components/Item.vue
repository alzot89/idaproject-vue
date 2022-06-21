<template>
  <li>
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
  }
}

</script>

<style>
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
</style>