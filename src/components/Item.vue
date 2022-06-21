<template>
  <li>
    <img class="item__image" :src="item.imageUrl" :alt="item.name">
    <h2 class="item__name">{{ item.name }}</h2>
    <p class="item__description">{{ item.description }}</p>
    <p>{{ item.price }}</p>
  </li>
</template>

<script>
export default {
  name: 'ListItem',
  props: ['item']
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