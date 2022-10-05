<template>
  <div class="main">

    <div class="top">
      <MyHead title="购物车案例" background="#2277fe"></MyHead>
    </div>

    <MyGoods v-for="item in list" :key="item.id" :obj="item"></MyGoods>

    <footer>
      <MyFooter @changeAll="allFn" :list="list"></MyFooter>
    </footer>
  </div>
</template>

<script>
  import MyGoods from './components/MyGoods.vue';
  import MyHead from './components/MyHead.vue';
  import MyFooter from './components/MyFooter.vue';
export default {
  data() {
    return {
      list: [],//商品所有数据
    };
  },
  components:{
    MyGoods,MyHead,MyFooter
  },
  methods:{
    allFn(bool){
      this.list.forEach(item=>item.goods_state=bool)
    }
  },
  created(){
    this.$axios({
      url:'/api/cart'
    }).then((res)=>{
      console.log(res);
      this.list = res.data.list
    })
  }                                
}
</script>

<style lang="less">
  *{
    margin: 0;
    padding: 0;
    list-style: none;
  }
  .main{
    padding: 60px 0 55px 0;
  }
  .top{
    position: fixed;
    top: 0;
    left: 0;
    z-index: 999;
  }
  footer{
    position: fixed;
    bottom: 0;
    left: 0;
    margin-top: 55px;
    width: 100%;
    height: 55px;
    background-color: #fff;
    line-height: 55px;
    border-top: 2px solid  #e1ece9;
    z-index: 999;
  }
  
</style>