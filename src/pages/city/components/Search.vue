<template>
<div class="search">
    <div class="search">
       <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音" />
    </div>
    <div class="search-content" ref="search">
        <ul>
            <li class="search-item  border-bottom"
             v-for="item of list" 
             :key="item.id"
             @click="handleCityClick(item.name)"
             >
             {{item.name}}
             </li>
        </ul>
    </div>

</div>
   
    
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'
    export default {
        name:'CitySearch',
         props:{
          cities:Object
        },
        methods:{
            handleCityClick (city) {
              this.changeCity(city)
              },
              ...mapMutations(['changeCity'])
        },
         data () {
            return {
                keyword:'',
                list:[],
                timer:null
            }
        },
       
       
        watch:{
            keyword () {
             if(this.timer){          
              clearTimeout(this.timer)
             }
             this.timer=setTimeout(()=>{
                 const result=[]
                 for(let i in this.cities){
                 this.cities[i].forEach((value)=>{
                     if(value.spell.indexOf(this.keyword) > -1 ||
                     value.name.indexOf(this.keyword) > -1){
                      result.push(value)
                     }
                 })
                 }
                 console.log(result)
                 this.list=result
             },100)
            }
        },
        mounted () {
            this.scroll=new Bscroll(this.$refs.search)
        }
    }
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.search
  height:.72rem
  padding:0 .1rem
  background:$bgColor
  .search-input 
    box-sizing:border-box
    width:100%
    height .62rem
    padding:0 .1rem
    line-height:.62rem
    text-align:center
    border-radius:.06rem
    color:#666
.search-content
  z-index:1
  overflow:hidden
  top:1.58rem
  left:0
  right:0
  bottom:0
  background:#eee
  .search-item
    line-height:.62rem
    padding-left:.2rem
    background:#fff
    color:#666
</style> 