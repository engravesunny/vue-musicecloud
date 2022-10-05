<template>
    <div >
        <ul>
            <li class="good">
                <div class="left">
                    <input type="checkbox" v-model=obj.goods_state :id="obj.id">
                    <label :for="obj.id">
                        <img :src=obj.goods_img :alt=obj.goods_name>
                    </label>
                </div>
                <div class="right">
                    <div class="title" v-text=obj.goods_name>
                    </div>
                    <div class="count">
                        <MyCount :obj="obj"></MyCount>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    import MyCount from './MyCount.vue';
export default {
    props:['obj'],
    components:{
        MyCount
    }
}
</script>

<style scoped lang="less">
    *{
        margin: 0;
        padding: 0;
        list-style: none;
    }
    .good{
        width: 100%;
        height: 100px;
        padding: 20px 0 20px 0;
        overflow: hidden;
        border-bottom: 2px solid #e8f0ed;
        .left{
            display: flex;
            float: left;
            margin: -9px 0;
            width: 40%;
            input{
                margin:5px;
                float: left;
            }
            img{
                float: left;
                width:80%;
                border-radius: 10px;
            }
        }
        .right{
            position: relative;
            width: 60%;
            height:100%;
            float: right;
            .title{
                margin: 0 0 5px 0;
                float: left;
                width: 100%;
                font-weight: 900;
            }
            .count{
                width: 100%;
                position: absolute;
                right: 0;
                bottom: 0;
            }
        }
    }
</style>