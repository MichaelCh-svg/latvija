<template>
  <div class="wrapper">
    <div class="products">
      <!-- <router-link v-for="product in products" :key="product.id" :to="'/product/' + product.id"> -->
      
    
        <div class="product" v-for="product in products" :key="product.id">
        <!-- <div class="product"> -->
          <div class="info">
            <h1>{{ product.name }}</h1>
            <p>{{ product.country }}</p>
          </div>
          <router-link :key="product.id" :to="'/product/' + product.id">
            <div class="image">
              <img :src="'/images/' + product.image" />
            </div>
          </router-link>
          <div class="price">
            <h2>{{ product.price }}</h2>
            <button class="auto" @click="cart(product)">{{product.quantity}} Thumbs up</button>
          </div>
        </div>
      <!-- </router-link> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "PortfolioList",
  props: {
    products: Array
  },
  methods: {
    cart(item) {
      item.quantity+=1;
      this.$root.$data.numItems+=1;
      if(item.quantity===1){
        this.$root.$data.cart.push(item);
      }
      
     // let index=this.$root.$data.cart.indexOf(item);
      
    }
  },
  computed: {}
};
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
  background: #f2921d;
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