<template>
    <div class="footer">
        <div class="left"><input type="checkbox" v-model="isAll">全选</div>
        <div class="mid">合计：<span> ￥ {{ allPrice }} </span></div>
        <div class="right"><button>结算( {{ allCount }} )</button></div>
    </div>
</template>

<script>
export default {
    props:['list'],
    computed:{
        isAll:{
            set(val){
                this.$emit('changeAll',val)
            },
            get(){
                return this.list.every(item=>item.goods_state==true)
            }
        },
        allCount(){
            return this.list.reduce((sum,item)=>{
                if(item.goods_state)sum+=item.goods_count;
                return sum;
            },0)
        },
        allPrice(){
            return this.list.reduce((sum,item)=>{
                if(item.goods_state){
                    sum += item.goods_count * item.goods_price;
                }
                return sum;
            },0)
        }
    }
}
</script>

<style scoped lang="less">
    .footer{
        .left{
            margin: 6px;
            float: left;
            width: 25%;
            input{
                margin: 5px;
            }
        }
        .mid{
            margin: 6px;
            float: left;
            width: 40%;
            span{
                width: 100%;
                color: red;
            }
        }
        .right{
            text-align: center;
            margin: 6px;
            float: right;
            width: 25%;
            button{
                border: 0;
                width: 85px;
                height: 32px;
                border-radius: 20px;
                background-color: #0675ff;
                color: #fff;
            }
        }
    }
</style>