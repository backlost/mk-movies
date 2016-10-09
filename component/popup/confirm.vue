<style scoped lang="sass">
    @import "../scss/variable";
    @import "../scss/mixin";
    @import "../scss/component";
    .confirm {
        position: fixed;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        z-index: 6;
        .confirm-btn {
            margin: 0;
            appearance: none;
            border: none;
            background-color: transparent;
            font-size: shift(32);
            color: #3d82f7;
            transition: background-color 100ms ease-in;
            &:active,
            &:focus {
                 outline: none;
                 background-color: rgba(0, 0, 0, 0.1);
            }
        }
        .confirm-dialog {
            position: fixed;
            top: 50%;
            left: 50%;
            right: 0;
            /*margin: 0 auto;*/
            z-index: 6;
            transform: translate(-50%, -50%);
            background-color: #fafafa;
        }
        .confirm-title {
            font-weight: normal;
        }
        .confirm-content{
            padding:0 shift(80);
            font-size:shift(30);
            line-height:shift(36);
            color: #5a5a5a;
        }
        p {
            margin-bottom:shift(50);
        }
        .confirm-occupied{
            display: block;
            margin: shift(116) auto shift(30);
            max-width:50%;
        }
        &.confirm-android {
            .confirm-dialog {
                padding: shift(20);
                width: 560/750*100 + %;
                // min-height: shift(268);
            }
            .confirm-content{
                margin-bottom:shift(66);
                padding:0 shift(30);
            }
            .confirm-title {
                padding: shift(30);
                font-size: shift(32);
                line-height: 1.5;
                color: #787878;
            }
            .confirm-btn-wrapper {
                text-align: right;
            }
            .confirm-btn {
                padding: shift(20);
            }

            .confirm-btn-left {
                color: #5a5a5a;
            }
        }
        &.confirm-ios {
            .confirm-dialog {
                width: 610/750*100+%;
                border-radius: shift(14);
            }
            .confirm-title {
                line-height: 1.2;
                text-align: center;
                padding: shift(50) shift(30);
                color: #1e1e1e;
            }
            .confirm-btn-wrapper {
                overflow: hidden;
                /*display: flex;*/
                clear: both;
                @extend .border-top;
            }
            .confirm-btn {
                /*flex: 1;*/
                float: left;
                margin:0;
                width:50%;
                padding: shift(28) shift(20);
            }
            .confirm-btn-right{
                border-bottom-right-radius: shift(10);
            }
            .confirm-btn-left {
                position: relative;
                left:-1px;
                @extend .border-right;
                color: #5a5a5a;
                border-bottom-left-radius: shift(10);
            }
            .confirm-content{
                text-align: center;
            }
            &.confirm-theme-blue{
                .confirm-btn-wrapper{
                    border: none;
                    background-image: none;
                }
                .confirm-dialog{
                    background-color: #395ff6;
                }
                .confirm-title{
                    color: #fff;
                    font-size:shift(38);
                }
                .confirm-content{
                    text-align: center;
                    color: rgba(255,255,255,0.7);
                }
                .confirm-btn{
                    background-color: rgba(0,0,0,0.3);
                    background-image: none;
                    color: #fff;
                }
                .confirm-btn-left{
                    color: rgba(255, 255, 255, 0.7);
                }
             }
        }
    }
</style>
<template>
    <div v-bind:class="classObject" v-show="show">
        <mask :show="show"></mask>
        <div class="confirm-dialog">
            <img :src="occupied" class="confirm-occupied" v-if="occupied">
            <h4 class="confirm-title" v-html="title"></h4>
            <p class="confirm-content" v-if="content">
                {{content}}
            </p>
            <div class="confirm-content" v-else>
                <slot></slot>
            </div>
            <div class="confirm-btn-wrapper">
                <button class="confirm-btn confirm-btn-left" v-html="leftButton" v-on:click="clickLeftBtn"></button>
                <button class="confirm-btn confirm-btn-right" v-html="rightButton" v-on:click="clickRightBtn"></button>
            </div>
        </div>
    </div>
</template>

<script>
import Mask from './mask.vue';

export default {
    components:{
        mask:Mask
    },
    props: {
        show:{
            default: true,
            twoWay:true,
            required:true,
        },
        title:{
            default:'是否确定'
        },
        content:{

        },
        leftButton:{
            default:'取消'
        },
        rightButton:{
            default:'确定'
        },
        closeButton:{
            default:false
        },
        occupied:{
            default:''
        },
        platform:{

        },
        theme:{

        },
        isPushHistory:{
            default:true
        }
    },
    created:function(){
    },
    watch:{
        show:function () {
            if(this.isPushHistory){

                if(!this.isPushState && this.show == true){
                    this.isPushState = true;
                    this.historyLength = history.length
                    try {
                        history.pushState('confirm-show', null , null);
                    } catch (error) {

                    }
                }
                if(this.isPushState && this.show == false){
                    if(history.state == 'confirm-show'){
                        this.isPushState = false;
                        history.back();
                    }
                }
                $(window).on('popstate',this.pushStateHandler);

            }
            

            if(this.show){
                $('body').css('overflow','hidden');
            }else{
                $('body').css('overflow','auto');
            }
        }
    },
    computed:{
        device:function (){
            if(this.platform){
                return this.platform;
            }else{
                return navigator.userAgent.match('Android') ? 'android':'ios'
            }
        },
        classObject:function (){
            var o = {
                'confirm':true,
                'confirm-ios':this.device == 'ios',
                'confirm-android':this.device == 'android',
            };
            if(this.theme){
                var theme = `confirm-theme-${this.theme}`;
                o[theme] = true;
            }
            return o
        },
    },
    methods:{
        pushStateHandler : function (){
            if(this.isPushState){
                this.show = false;
                this.$emit('cancel',{target:'back'});
                if(this.isPushHistory){
                    this.isPushState = false;
                    $(window).off('popstate',this.pushStateHandler);
                }
            }
        },
        clickLeftBtn:function (){
            this.show = false;
            this.$emit('cancel',{target:'left'})
        },
        clickRightBtn:function (){
            this.show = false;            
            this.$emit('sure')            
        }
    },
    beforeDestroy:function () {
        $('body').css('overflow','initial');
    }
}
</script>