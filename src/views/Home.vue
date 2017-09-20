<template>
 <div>
  <mt-header fixed :title="appname"></mt-header>
  <mt-navbar v-model="selected" >
      <mt-tab-item id="0">头条</mt-tab-item>
   <mt-tab-item id="1">娱乐</mt-tab-item>
  <mt-tab-item id="2">社会</mt-tab-item>
  <mt-tab-item id="3">生活</mt-tab-item>
</mt-navbar>

 <div class="page-tab-container"> 
<mt-tab-container v-model="selected">
   
     <mt-tab-container-item id="0" >
    <mt-cell v-for="n in datas" 
    :key="n.index"
   
    >
       <span class="news-title">{{n.title}}</span>
       
     </mt-cell>

  </mt-tab-container-item>
  <mt-tab-container-item id="1">
    <mt-cell v-for="n in 10" 
    :key="n.index"
    :title="'内容 ' + n" />
  </mt-tab-container-item>
  <mt-tab-container-item id="2">
    <mt-cell v-for="n in 4" 
    :key="n.index"
    :title="'测试 ' + n" />
  </mt-tab-container-item>
  <mt-tab-container-item id="3">
    <mt-cell v-for="n in 6" 
    :key="n.index"
    :title="'选项 ' + n" />
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
              datas:[]
          }
      },
      mounted (){
            
          
            this.getdata()

      },

    
     methods :{

          getdata () {

                this.$ajax.get("api/get?channel=%e5%a4%b4%e6%9d%a1&num=20&start=0&appkey=3dacf6c8db719ac1ce24eb8d290cd5d8").then((response) => {
                         
       
                         return  this.datas=response.data.result.result.list
                   })
                  
                           
                           //this.data=data.result.result.list;
                    




          }





     }


}
</script>
<style>
.news-img{

   float:left;
   
}
.news-title{
  float:right;
  font-size: 2rem;
}


</style>


