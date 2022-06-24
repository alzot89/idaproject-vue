<template>
  <select class="sorter" v-model="option" @change="onChange(option)">
    <option v-for="(option, index) in options" :value="option.value" :key="index">{{ option.label
    }}</option>
  </select>
</template>

<script>
export default {
  name: 'ItemSorter',
  data() {
    return {
      option: 'default',
      options: [
        {
          label: 'По умолчанию',
          value: 'default'
        },
        {
          label: 'По наименованию',
          value: 'name'
        },
        {
          label: 'По цене (от меньшего к большему)',
          value: 'min'
        },
        {
          label: 'По цене (от большего к меньшему)',
          value: 'max'
        }
      ]
    }
  },
  methods: {
    onChange(option) {
      this.$emit('sorting', option)
    }
  }
}
</script>

<style>
.sorter {
  margin-left: auto;
  padding: 10px 0 11px 16px;
  max-width: 260px;
  height: 36px;
  background-color: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: 0;
  outline-style: none;
  font-family: 'Source Sans Pro';
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
}
</style>
