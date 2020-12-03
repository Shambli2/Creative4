<template>
<div class="wrapper">
  <div class="products">

    <div class="product" v-for="item in items" :key="item.id">
      <div class="info">
        <h1>{{item.title}}</h1>
        <h2>{{item.description}}</h2>
      </div>
      <div class="image">
        <img :src="item.path" />
      </div>
      <div class="price">
        <h2>${{item.price}}</h2>
        <button class="auto" v-on:click="addToCart(item)">Add to Cart</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Browse',

  data() {
    return {
     items: [],
    }
  },
  created() {
    this.getItems();
  },
  methods: {
   async getItems() {
     try {
       let response = await axios.get("/api/items");
       this.items = response.data;
       return true;
     } catch (error) {
       console.log(error);
     }
   },
   addToCart(item) {
    this.$root.$data.cart.push(item);
   }
 }
}
</script>

<style scoped>
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
  background: #DA982C;
  color: #000;
  padding: 10px 30px;
  height: 80px;
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
