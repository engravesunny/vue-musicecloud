<template>
    <div>
        <div class="price">
            ￥{{ obj.goods_price }}
        </div>
        <div class="btn">
            <button :disabled="obj.goods_count == 1" @click="obj.goods_count--">-</button>
            <input type="text" v-model.number=obj.goods_count>
            <button @click="obj.goods_count++">+</button>
        </div>
    </div>
</template>

<script>
export default {
    props:['obj'],
    methods:{
        pop(){
            if(this.num>=1){
                this.num--;
            }
            else{
                return;
            }
        }
    },
    watch:{
        obj:{
            deep:true,
            handler(){
                if(this.obj.goods_count < 0 || this.obj.goods_count == '-'){
                    this.obj.goods_count = 1
                }
            }
        }
    }
}
</script>

<style scoped lang="less">
    .price{
        width: 30%;
        float: left;
        color: red;
        font-weight: 900;
    }
    .btn{
        float: right;
        input{
            text-align: center;
            width: 30px;
            height: 18px;
            border: 0;
            border-top: 1px solid black;
            border-bottom: 1px solid black;
            
        }
        button{
            width: 20px;
            height: 20px;
        }
    }
</style>