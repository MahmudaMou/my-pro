<template>
<!-- <div class="container"> -->
<div >
<h2 class="text-center" style="margin-top:-10px; margin-left:250px; padding-bottom: 20px;">Tasks To Do</h2>
 <div>
  
  <b-tabs content-class="" >

    <b-tab title="High Priority" active>
        <div class="row-container">
       <div class="com" v-for="hight in high"
      :key="hight.id">
            
       <div :class="'product-inner ' + hight.color ">
         <div class="product-text-wrap">
           <h2 class="bg-text">{{hight.bgtext}}</h2>
         </div>
         <div class="product-image-wrap">
           <img :src="hight.image" class="image" style="height:140px;width:170px;">
         </div>
         <div class="product-detail">
           <h2>{{hight.title}}</h2>
           <p>{{hight.detail}}</p>
         </div>
       </div>
       </div>
</div>
  </b-tab >
    <b-tab title="Mid Priority">
          <div class="row-container">
      <div class="com" v-for="midp in products"
      :key="midp.id">
            
       <div :class="'product-inner ' + midp.color ">
         <div class="product-text-wrap">
           <h2 class="bg-text">{{midp.bgtext}}</h2>
         </div>
         <div class="product-image-wrap">
           <img :src="midp.image" class="image">
         </div>
         <div class="product-detail">
           <h2>{{midp.title}}</h2>
           <p>{{midp.detail}}</p>
         </div>
       </div>
       </div>
       </div>
    </b-tab>


    <b-tab title="Low priority">
      <div class="row-container">
      <div class="com" v-for="lowp in low"
      :key="lowp.id">
            
       <div :class="'product-inner ' + lowp.color ">
         <div class="product-text-wrap">
           <h2 class="bg-text">{{lowp.bgtext}}</h2>
         </div>
         <div class="product-image-wrap">
           <img :src="lowp.image" class="image" style="height:140px;width:170px;">
         </div>
         <div class="product-detail">
           <h2>{{lowp.title}}</h2>
           <p>{{lowp.detail}}</p>
         </div>
         </div>
       </div>
       </div>
    </b-tab>
    
  </b-tabs>
 
</div>
 
</div>    
</template>
<script>



export default{
  name: 'ProductPage',


 
  props: {
  
  products:{
    type: Array,
    default: null,
  },
  high:{
    type: Array,
    default: null,
  },
   low:{
    type: Array,
    default: null,
  } 
  }

}
</script>

<style>
.row-container{
  display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;


}
.com{
 display: flex;
       /* width: 356px; */
      min-height: 132px;
      /* background: #e6f7f0; */
      border-radius: 12px;
      align-items: center;
      justify-content: center;
      padding: 25px 15px;
      /* padding: 0 0 0 20px; */
      flex-basis: calc(50.333% - 40px/3);
 
}
.product-inner{
  position: relative;
  padding: 25px;
  box-shadow: 0px 0px 16px rgba(0, 0, 0,0.25);

}
.product-inner.red{
    background-image: linear-gradient(to bottom right, #dd7972,#8a210f);

}
.product-inner.yellow{
    background-image: linear-gradient(to bottom right, #dfe13c,#424907);

}
.product-inner.green{
    background-image: linear-gradient(to bottom right, #2ef445,#0b3714);

}
.product-inner.blue{
    background-image: linear-gradient(to bottom right, #503098,#2fb0ae );

}
.product-inner.pink{
    background-image: linear-gradient(to bottom right, #e86cbf,#3599c7 );

}
.product-image-wrap .image{
  width: 100%;
  filter: drop-shadow(0px 0px 12px rgba(0,0,0,0.25));
}
.product-image-wrap{
  position: relative;
  z-index: 1;
  transform-origin: center;
}
.product-text-wrap{
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  overflow: hidden;
}
.product-text-wrap h2{
  color: #313131;
  font-size: 128px;
  font-weight: 900;
  opacity: 0.2;
  transform-origin: center;
}
.product-detail {
    background-color: #FFF;
    padding: 25px;
    margin: 0px -25px -25px;
    
  }
  .product-detail h2 {
    font-size: 24px;
    font-weight: 700;
    color: #676767;
    margin-bottom: 15px;
  }
  .product-detail p {
    font-size: 14px;
    line-height: 1.5;
    font-weight: 300;
    color: #676767;
  }

</style>
