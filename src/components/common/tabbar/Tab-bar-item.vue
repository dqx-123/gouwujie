<template>
    <div class="tab-bar-item" @click="itemClick">

        <slot v-if="!isActived" name="slot-img"></slot>
        <slot v-else name="slot-active-img"></slot>
        <div :style="activeStyle">
            <slot name="slot-text"></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: "tab-bar-item",
        data(){
            return{
                // isActived:false
            }
        },
        computed:{
            isActived(){
                return this.$route.path.indexOf(this.path)!==-1
            },
           activeStyle(){
                // return this.isActived?{color:this.activeColor}:{}
               return this.isActived?{color:this.activeColor}:{}
           }
        },
        props:{
            path:String,
            activeColor:{
                type:String,
                default:"blue"
            }
        },
        methods:{
            itemClick(){
                console.log(this.isActived)
                this.$router.push(this.path)
            }
        }
    }
</script>

<style scoped>

    #tabbar{
        width: 100%;
        position: fixed;
        bottom: 0;
        display: flex;
        justify-content: space-around;
        background: #f6f6f6;
        box-shadow: 0 -1px 1px rgba(100,100,100,0);
    }
    .tab-bar-item{
        height: 49px;
        text-align: center;
    }
    .active{
        color:deepskyblue;
    }
    .tab-bar-item img{
        width: 24px;
        height: 24px;
    }
</style>
