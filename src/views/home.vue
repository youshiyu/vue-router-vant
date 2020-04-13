<template>
    <div>
        <lg-header :leftArrow="false" :titleType="1" title="首页"></lg-header>
        <div class="list">
            <lg-tab :title="title" :scrollerable="false" :animated="true" @tab-change="tabChange" @on-refresh="onRefresh" 
            @on-infinite="onInfinite">
                <!-- <p v-for="i in num"   :key="i">{{content[i]}}</p> -->
                <p>{{content[num]}}</p>
            </lg-tab>
        </div>
      
    </div>
</template>

<script>
export default {
    name:"Home",
    data(){
        return {
            title:[
                {id:'0',title:'音乐推荐'},
                {id:'1',title:'热门新闻'},
                {id:'2',title:'编程学习'},
            ],
            num: 1,
            content:['','冬眠-思南','4/12日热点新闻','javascript']
        }
    },
    methods:{
        tabChange(index,title){
            console.log("index:"+index+":num"+this.num)
          
            if(this.num==3)
            this.num=0;
          this.num ++;
        },
        onRefresh(done){
            setTimeout(()=>{
              //  done();
            },1500)
        },
        onInfinite(done){
            setTimeout(()=>{
                this.num += 50;
                //done();
            },1500)
        }
    },
}
</script>
<style lang="scss" scoped>
.list{
    height: 100%;
    padding-top: 46px;
}
</style>