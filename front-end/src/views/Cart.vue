<template>
<div>

  <h1 class = "header" v-show="this.$root.$data.cart.length === 0">Cart is Empty</h1>

  <div class="wrapper">
    <div class="products">
      <div class="product" v-for="item in cartArray" :key="item.id">

        <div class="info">
          <h1>{{item.title}}</h1>
          <h2>{{item.description}}</h2>
        </div>
        <div class="image">
          <img :src="item.path" />
        </div>
        <div class="price">
          <h2>${{item.price}}</h2>
          <button class="auto" v-on:click="removeFromCart(item)">Remove</button>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Cart',
  props: {
    cart: Array,
  },

  computed: {
    cartArray() {
      return this.$root.$data.cart;
    },
  },
  methods: {
    removeFromCart(item) {
      this.$root.$data.cart.splice(this.$root.$data.cart.indexOf(item),1);
    }
  },

}
</script>

<style scoped>
.header {
  text-align: center;
}
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #F96988;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}
h1 {
  font-size: 30px;
}
.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>
