<style scoped lang="sass">
    @import "../scss/variable";
    @import "../scss/mixin";
    @import "../scss/component";
    .alert {
        position: fixed;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        z-index: 6;
        .alert-btn {
            appearance: none;
            border: none;
            background-color: transparent;
            font-size: shift(32);
            color: #3c6df7;
        }
        .alert-dialog {
            position: fixed;
            top: 50%;
            left: 50%;
            right: 0;
            z-index: 6;
            transform: translate(-50%, -50%);
            background-color: #fafafa;
            overflow: hidden;
        }
        .alert-title {
            font-weight: normal;
        }
        .alert-content {
            padding: shift(30) shift(55);
            font-size: shift(26);
            line-height: shift(36);
            color: #969696;
        }
        .alert-occupied {
            display: block;
            margin: shift(116) auto shift(30);
            max-width: 50%;
        }
        .alert-btn {
            font-size: shift(32);
            transition: background-color 100ms ease-in;
            margin: 0;
            &:active,
            &:focus {
                outline: none;
                background-color: rgba(0, 0, 0, 0.1);
            }
        }
        &.alert-android {
            .alert-dialog {
                padding: shift(20);
                width: 560/750*100 + %;
                // min-height: shift(268);
            }
            .alert-title {
                padding: shift(30) shift(30) 0;
                font-size: shift(32);
                line-height: 1.5;
                color: #787878;
            }
            .alert-btn-wrapper {
                text-align: right;
            }
            .alert-btn {
                padding: shift(20);
            }
            .alert-btn-left {
                color: #5a5a5a;
            }
        }
        &.alert-ios {
            .alert-dialog {
                width: 610/750*100+%;
                border-radius: shift(14);
            }
            .alert-title {
                line-height: 1.2;
                text-align: center;
                font-size: shift(38);
                /*padding: shift(30);*/
                margin-top: shift(70);
                color: #1e1e1e;
            }
            .alert-btn-wrapper {
                @extend .border-top;
            }
            .alert-btn {
                display: block;
                box-sizing: border-box;
                width: 100%;
                padding: shift(31) shift(20);
            }
            .alert-btn-left {
                @extend .border-right;
                color: #5a5a5a;
            }
            .alert-content {
                text-align: center;
            }
            .alert-occupied{
                + .alert-title{
                    margin-top: shift(40);
                }
            }
            &.alert-theme-blue {
                .alert-dialog {
                    background-color: #3660f6;
                }
                .alert-btn{
                    background-color: #2e53d6;
                    color: #fff;
                }
                .alert-btn-wrapper{
                    background: none;
                    border-top: none;
                }
                .alert-title{
                    color: #fff;
                }
                .alert-content{
                    color: rgba(255,255,255,.4);
                }
            }
        }
    }
</style>
<template>
    <div v-bind:class="classObject" v-show="show" transition="fade">
        <mask :show="show"></mask>
        <div class="alert-dialog">
            <img :src="occupied" class="alert-occupied" v-if="occupied">
            <h4 class="alert-title" v-html="title"></h4>
            <p class="alert-content" v-if="content">
                {{content}}
            </p>
            <div class="alert-content" v-else>
                <slot></slot>
            </div>
            <div class="alert-btn-wrapper">
                <button class="alert-btn" v-on:click.prevent="clickRightBtn">{{button}}</button>
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

        },
        occupied:{
            default:''
        },
        theme:{

        },
        content:{

        },
        button:{
            default:'确定'
        },
        platform:{

        },
    },
    created:function(){
    },
    watch:{
        show:function () {
            if(!this.isPushState && this.show == true){
                this.isPushState = true;
                this.historyLength = history.length
                try {
                    history.pushState('alert-show', null , null);                    
                } catch (error) {
                    
                }
            }
            if(this.isPushState && this.show == false){
                if(history.state == 'alert-show'){
                    this.isPushState = false;                    
                    history.back();
                }
            }
            
            $(window).on('popstate',this.pushStateHandler);

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
                'alert':true,
                'alert-ios':this.device == 'ios',
                'alert-android':this.device == 'android'
            };

            if(this.theme){
                var theme = `alert-theme-${this.theme}`;
                o[theme] = true;
            }
            return o
        },
    },
    methods:{
        pushStateHandler : function (){
            if(this.isPushState){
                this.show = false;
                this.isPushState = false;    
                this.$emit('cancel');                                                
                $(window).off('popstate',this.pushStateHandler);
            }
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