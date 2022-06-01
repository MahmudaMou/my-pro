<template>
<div>
        <div>
         <HeaderPart/>
  </div>
  <div id="app" class="container">
   <div class="row">
      
      <div class="col-md-6 product">
  <ProductPage :products = "products" :high = "high" :low = "low"/> 
  </div>
  
  <div class="col-md-4">
           <TodoApp/>
           </div> 
    </div>
  </div>
</div>
 

</template>

<script>
import axios from 'axios';
 
import TodoApp from './components/TodoApp.vue'
import ProductPage from './components/ProductPage.vue'
import HeaderPart from './components/HeaderPart.vue'



export default {
  name: 'App',
  components: {
    ProductPage,
    HeaderPart,
    TodoApp,

},
  data(){
    return {
      products:[],
      high:[],
      low:[],
      info: []
    }
  },

  
  created(){
        axios.get(`/items`)
       .then(res => {
                  
                    this.products = res.data.data.mid;
                    this.high = res.data.data.high;
                    this.low = res.data.data.low;
       })
       .catch(error => console.log(error))
  }
      
}
</script>
<style>

   *{
     margin:0;
     padding: 0;
     box-sizing: border-box;

   }
   body{
     font-family: 'montseratt', sans-serif;
   }
   main{
     margin-top: 10px;
     width:100vw;
     min-height: 100vh;
     overflow: hidden;
     background-color: aqua;
     /* display: flex; */
   
   }
   .product{
   
     /* max-width: 1280px; */
     /* width: 100px; */
 
     padding-top: 50px;
     padding-left: 50px;
     margin-left: -50px;
     margin-right: 150px;
    

     
  
   }
   
</style>


