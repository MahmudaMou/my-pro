<template>
<div >
<h2 class="text-center" style="margin-top:-10px; margin-left:250px; padding-bottom: 20px;">Tasks To Do</h2>
 <div>
   <div>
    
     
  <ul class="nav nav-tabs" pills >
     <TabNav v-for="tab in tabs" :key="tab" class="nav-item">
  <a class="nav-link" :class="{ active: tab === selected }" @click="setTab(tab)"
    >{{ tab }}</a>
</TabNav> 
  </ul>


  
        <tab v-on="selectContent()">
       <div class="row-container">
       <div class="com" v-for= "data in content"
      :key="data .id">
            
       <div :class="'product-inner ' + data .color ">
         <div class="product-text-wrap">
           <h2 class="bg-text">{{data .bgtext}}</h2>
         </div>
         <div class="product-image-wrap">
           <img :src="data .image" class="image" style="height:140px;width:170px;">
         </div>
         <div class="product-detail">
           <h2>{{data.title}}</h2>
           <p>{{data.detail}}</p>
         </div>
       </div>
       
       </div>   
</div>
</tab>

</div>

</div>
 
</div>    
</template>
<script>



export default{
  name: 'ProductPage',
  props: {
  
  mid:{
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
  },
  data(){
    return{
      selected: 'high priority',
      tabs: ['high priority','mid priority','low priority'],
      content:[],
    };

  },
  methods:{
         selectContent(){
         if(this.selected === this.tabs[0]){
         this.content = this.high;
         }
         else if(this.selected === this.tabs[1]){
             this.content = this.mid;
        }
         else if(this.selected === this.tabs[2]){
         this.content = this.low;
        }
      },
    
      setTab(tab){

        this.selected = tab;
      },
      
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
.nav-tabs .nav-item.show .nav-link, .nav-tabs .nav-link.active {
  background-image: linear-gradient(45deg, #1cd164, #e7c623);
  border-color: #1b5794;
  color: #fcfafa;
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
