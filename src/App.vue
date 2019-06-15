<template>
  <div id="app">
    <navbar @search="search"></navbar>
    <div class="container">
      <div class="row">
        <div class="col-sm-9">
          <inventory @newItemAdded="addToCart" :items="items"></inventory>
        </div>
        <div class="col-sm-3">
          <cart @removeFromCart="removeItem" :items="carts"></cart>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import Cart from "./components/Cart";
import Inventory from "./components/Inventory";

import data from "./data";
export default {
  components: {
    Navbar,
    Cart,
    Inventory
  },
  data() {
    return {
      items: [],
      carts: []
    };
  },
  mounted() {
    this.items = data;
    console.log(data);
  },
  methods: {
    addToCart(item) {
      this.carts.push(item);
    },
    removeItem(index) {
      this.carts.splice(index, 1);
    },
    search(keyword) {
      this.items = data.filter(item => {
        return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1;
      });
    }
  }
};
</script>

<style>
.container {
  padding-top: 10px;
}
.card {
  margin: 2px;
}
</style>
