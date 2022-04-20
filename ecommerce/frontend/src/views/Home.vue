<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div>
      Listado de productos
      <div v-for="product in products" :key="product.id">
        {{ product.name }}
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import url from '../utils/api'

export default {
  name: 'Home',
  components: {
  },
  
  data(){
    return  {
      products: []
    }

  },

  created() {
    fetch(url('/products?_page=2&_limit=5'))
    .then(response => response.json())
    .then(data => {
      console.log(`data ${data}`)
      this.products = data
    })
  },
}
</script>
