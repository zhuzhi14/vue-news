<template>
 <div>
  <mt-header fixed :title="appname"></mt-header>
  <mt-navbar v-model="selected" >
    <mt-tab-item id="0"><span class="news-bar">头条</span></mt-tab-item>
   <mt-tab-item id="1"><span class="news-bar">娱乐</span></mt-tab-item>
  <mt-tab-item id="2"><span class="news-bar">新闻</span></mt-tab-item>
  <mt-tab-item id="3"><span class="news-bar">体育</span></mt-tab-item>
   <mt-tab-item id="4"><span class="news-bar">科技</span></mt-tab-item>
    <mt-tab-item id="5"><span class="news-bar">财经</span></mt-tab-item>
</mt-navbar>
  <div  v-if="show"  class="showload">

          页面加载中

   </div>
 <div class="page-tab-container"> 
<mt-tab-container v-model="selected">
   
     <mt-tab-container-item id="0" >
     <ul>  
    <li v-for="n in datas" 
    :key="n.index"
    
    >
       <div class="news-con">
          
         <div class="news-img"><img :src="n.pic"></div>
         
         <div class="news-title">
           
           <span>{{n.title}}</span>
          
         </div>
         <div class="news-src">
         <span>{{n.src}}</span>  
          <span>{{n.time}}</span>
         </div>
         </div>
        <hr />
     </li>
     </ul>
 

  </mt-tab-container-item>
  
  <mt-tab-container-item id="1">
      <ul>  
    <li v-for="n in datas" 
    :key="n.index"
    
    >
       <div class="news-con">
          
         <div class="news-img"><img :src="n.pic"></div>
         
         <div class="news-title">
           
           <span>{{n.title}}</span>
          
         </div>
         <div class="news-src">
         <span>{{n.src}}</span>  
          <span>{{n.time}}</span>
         </div>
         </div>
        <hr />
     </li>
     </ul>
  </mt-tab-container-item>
  <mt-tab-container-item id="2">
    <ul>  
    <li v-for="n in datas" 
    :key="n.index"
    
    >
       
       <div class="news-con">
          
         <div class="news-img"><img :src="n.pic"></div>
         
         <div class="news-title">
           
           <span>{{n.title}}</span>
          
         </div>
         <div class="news-src">
         <span>{{n.src}}</span>  
          <span>{{n.time}}</span>
         </div>
         </div>
        <hr />
     </li>
     </ul>
  </mt-tab-container-item>
  <mt-tab-container-item id="3">
    <ul>  
    <li v-for="n in datas" 
    :key="n.index"
    
    >
       <div class="news-con">
          
         <div class="news-img"><img :src="n.pic"></div>
         
         <div class="news-title">
           
           <span>{{n.title}}</span>
          
         </div>
         <div class="news-src">
         <span>{{n.src}}</span>  
          <span>{{n.time}}</span>
         </div>
         </div>
        <hr />
     </li>
     </ul>
  </mt-tab-container-item>
    <mt-tab-container-item id="4">
    <ul>  
    <li v-for="n in datas" 
    :key="n.index"
    
    >
       <div class="news-con">
          
         <div class="news-img"><img :src="n.pic"></div>
         
         <div class="news-title">
           
           <span>{{n.title}}</span>
          
         </div>
         <div class="news-src">
         <span>{{n.src}}</span>  
          <span>{{n.time}}</span>
         </div>
         </div>
        <hr />
     </li>
     </ul>
  </mt-tab-container-item>
    <mt-tab-container-item id="5">
   <ul>  
    <li v-for="n in datas" 
    :key="n.index"
    
    >
       <div class="news-con">
          
         <div class="news-img"><img :src="n.pic"></div>
         
         <div class="news-title">
           
           <span>{{n.title}}</span>
          
         </div>
         <div class="news-src">
         <span>{{n.src}}</span>  
          <span>{{n.time}}</span>
         </div>
         </div>
        <hr />
     </li>
     </ul>
  </mt-tab-container-item>
</mt-tab-container>
 </div> 
 </div>

</template>

<script>
export default {
      name:'Home',
      data (){

          return {

              appname:'猪猪news',
              selected:"0",
              items:['头条','娱乐','社会','生活'],
              datas:[],
              show:true
          }
      },
      mounted (){
            
          this.$nextTick(function(){
                
                  this.getdata();
                   this.show=false;
                  

          })
          
      },
      watch:{

          selected:function(){
                this.datas="";
                this.getdata()

          }



      },

    
     methods :{

          getdata () {
                 let  selecetedname=this.selected;
                 let  channel;
                 switch (selecetedname) {
                       case '0':
                       channel=encodeURI("头条");
                       break;
                       case '1':
                       channel=encodeURI("娱乐");
                       break;
                       case '2':
                       channel=encodeURI("新闻");
                       break;
                        case '3':
                       channel=encodeURI("体育");
                       break;
                        case '4':
                       channel=encodeURI("科技");
                       break;
                          case '5':
                       channel=encodeURI("财经");
                       break;

                   
                 }
                 console.log(selecetedname);
                 console.log(channel);
                


                this.$ajax.get("api/get?channel="+channel+"&num=20&start=0&appkey=3dacf6c8db719ac1ce24eb8d290cd5d8").then((response) => {
                         
       
                         return  this.datas=response.data.result.result.list
                   })
                  
                           
                           //this.data=data.result.result.list;
                    




          },
           





     }


}
</script>
<style>

.news-bar{
  font-size:2.5rem;
}
.news-title{
  
  font-size: 2.2rem;
  line-height: 4rem;
  height:4rem;
  width:80%;
  text-align:left;
  overflow:hidden;
text-overflow:ellipsis;
white-space:nowrap;
}

.news-src{
  
  font-size: 1rem;
  line-height: 5rem;
  height:4rem;
  width:80%;
  text-align:right;
  overflow:hidden;
text-overflow:ellipsis;
white-space:nowrap;

display: block;

}
img{
   height: 8rem;
   width: 8rem;
   float:left;
   padding-right:30px;

}

ul{
  
  list-style: none;
 
}



</style>


