<template>
  <ul class="list-group">
    <li class="list-group-item">
      <span class="item-name">Name</span>
      <span class="item-price float-right">Price</span>
    </li>
    <hr>
    <li v-for="(item, index) in items" :key="index" class="list-group-item">
      <span class="item-name">{{ item.title }}</span>
      <span class="item-price float-right">${{ item.price }}</span>
    </li>
    <hr>
    <li class="list-group-item">
      <span class="item-name">Total</span>
      <span class="item-price float-right">${{ totalPrice }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["items"],
  computed: {
    totalPrice() {
      let total = 0;
      this.items.forEach(item => {
        total += parseFloat(item.price);
      });
      return total;
    }
  }
};
</script>

<style>
</style>
