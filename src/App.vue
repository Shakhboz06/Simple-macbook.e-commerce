<template>
  <div id="app">
       <div class="heading">
      <h2>Supercharged for pros.</h2>
      <p>
        The most powerful MacBook Pro ever is here. With the blazing-fast M1 Pro
        or M1 Max chip — the first Apple silicon designed for pros — you get
        groundbreaking performance and amazing battery life. Add to that a
        stunning Liquid Retina XDR display, the best camera and audio ever in a
        Mac notebook, and all the ports you need. The first notebook of its
        kind, this MacBook Pro is a beast.
      </p>
    </div>
   <Products/>
  </div>
</template>

<script>
import Products from './components/Products.vue'

export default {
  name: 'App',
  data: () =>{

  },
  components: {
    Products
  },
  methods:{
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
