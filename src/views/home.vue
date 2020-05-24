<template>
    <div>
        <lg-header :leftArrow="false" :titleType="1" title="首页"></lg-header>
        <div class="list">
            <lg-tab :title="title" :scrollerable="false" :animated="true" @tab-change="tabChange"> 
               <div v-if="newshow">
                     <News></News>
               </div>
                <div v-else-if="songshow">
                     <Songs></Songs>
               </div>
              <div v-else-if="codeshow">
                  <Codelearning></Codelearning>
              </div>
            </lg-tab>
        </div>
    </div>
</template>

<script>
import News from "./news" 
import Songs from "./songs" 
import Codelearning from "./codelearning"
import Friends from "./friends"
export default {
    name:"Home",
    data(){
        return {
            title:[
                {id:'0',title:'热门新闻'},
                {id:'1',title:'音乐推荐'},
                {id:'2',title:'编程学习'},
            ],
            newshow :true,
            songshow:false,
            codeshow:false
        }
    },
    methods:{
        tabChange(index,title){
          console.log(index,title);
          if(index===0){
              this.newshow=true;
              this.songshow=false;
              this.codeshow=false;
          }
         else if(index===1){
              this.newshow=false;
              this.songshow=true;
              this.codeshow=false;
          }
          else  if(index===2){
              this.newshow=false;
              this.songshow=false;
              this.codeshow=true;
          }
        }
    },
     components:{
         News,Songs,Codelearning
     }
}
</script>
<style lang="scss" scoped>
.list{
    height: 100%;
    padding-top: 46px;
}
</style>