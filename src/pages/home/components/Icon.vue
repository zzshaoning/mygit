<template>
    <div class="icons">
      <swiper>

          <swiper-slide v-for="(page,index) of pages" :key="index">
       <div class="icon" v-for="item of page" :key="item.id">
           <div class="icon-img">
                <img class="icon-img-content" :src="item.imgUrl"/>
           </div>
          <p class="icon-desc">{{item.desc}}</p>
       </div>
       </swiper-slide>
        </swiper>
    </div>
</template>

<script>
    export default {
        name:"HomeIcon",
        data (){
        return {
         iconList:[
           {
          id:"0001",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
          desc:'景点门票'
        },
        {
          id:"0002",
          imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/a40ee278d67000f2a29d2e20f6a029b3.png',
          desc:'自然风光'
        },
        {
          id:"0003",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png",
          desc:'植物园'
        },
        {
          id:"0004",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:'故宫'
        },
        {
          id:"0005",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:'故宫'
        },
        {
          id:"0006",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:'故宫'
        },
        {
          id:"0007",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:'故宫'
        },
        {
          id:"0008",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:'故宫'
        },
        {
          id:"0009",
          imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:'故宫'
        }
        ]
        }
        },
        computed:{
          pages () {
            const pages=[]
            this.iconList.forEach((item,index)=>{
              const page=Math.floor(index/8)
              if(!pages[page]){
                pages[page]=[]
              }
              pages[page].push(item)
            })
            return pages
          }
        }
    }
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
.icons >>> .swiper-container
  height:0
  padding-bottom:50%
  .icon
    position:relative
    overflow:hidden
    float:left
    width:25%
    padding-bottom:25%
    .icon-img
      position:absolute
      top:0
      left:0
      right:0
      bottom .44rem
      box-sizing:border-box
      padding:.1rem
      .icon-img-content
        display:block
        margin:0 auto
        height:100%
    .icon-desc
      position:absolute
      left:0
      right:0
      bottom:0
      line-height:.44rem
      height:.44rem
      text-align:center
      color:$darkTextColor
      ellipsis() 
</style>