<script>
import axios from 'axios'

export default{
  data(){
    return{
      items:[]
    }
  },
  methods:{
    getData(){
      axios.get('https://api.nuxtjs.dev/beers').then((response) => {
        this.items = response.data
      })
    }
  },
  created(){
    this.getData()
  }

}
</script>
<template>
  <div v-for="item in items" :key="item" class="wrapper">
    <ul class="image_url">
      <img :src="item.image_url" :alt="item.title">
    </ul>
    <ul class="characters">
      <li class="name">{{ item.name }}</li>
      <li class="product_id">{{ item.product_id }}</li>
      <li class="size">{{ item.size }}</li>
      <li class="price">{{ item.price }}</li>
      <li class="category">{{ item.category }}</li>
      <li class="brewer">{{ item.brewer }}</li>
      <li class="country">{{ item.country }}</li>
    </ul>
  </div>
</template>

<style>
*{

  margin: 0;
  padding: 0;
  list-style: none;
  text-decoration: none;
  box-sizing: border-box;
}
.wrapper{
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.characters{
  margin-right: 180px;
}
.image_url{
  margin-left: 180px;
}
.name{
  font-size: 40px;
}
.product_id, .size, .price, .category, .brewer, .country{
  font-size: 21px;
}
</style>