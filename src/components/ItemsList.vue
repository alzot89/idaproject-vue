<template>

  <ul>
    <li v-for="(item, index) in items" :key="index">
      <img class="item__image" :src="item.imageUrl" alt="">
      <h2 class="item__name">{{ item.name }}</h2>
      <p class="item__description">{{ item.description }}</p>
      <p>{{ item.price }}</p>
    </li>
  </ul>

</template>

<script>
export default {
  name: 'ItemsList',
  props: ['items']
}

</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(3, 332px);
  gap: 16px;
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
</style>