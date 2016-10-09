<style scoped lang="sass">
    @import "../../../style/scss/variable";
    @import "../../../style/scss/mixin";
    
    .icon {
        float: none;
        display: inline-block;
        /*vertical-align: middle;*/
        width: 0.9375rem;
        height: 0.9375rem;
        &.icon-new {
            background-image: url(https://s.momocdn.com/w/u/img/2016/04/15/1460707810365-title-new-icon.png?_bid=1090);
            background-size: 100%;
            margin-bottom: -2px;
        }
        &.icon-elite {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/15/1460707810386-title-elite-icon.png?_bid=1090");
            background-size: 100%;
            margin-bottom: -2px;
        }
        &.icon-top {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/15/1460707810394-title-top-icon.png?_bid=1090");
            background-size: 100%;
            margin-bottom: -2px;
        }
        &.icon-loading {
            width: shift(32);
            height: shift(32);
            background-image: url("https://s.momocdn.com/w/u/img/03/10/1457603892170-ic_loading.png?_bid=1090");
            background-size: 100%;
            animation: rotate 1s ease-in-out infinite;
        }
        &.icon-admin {
            display: inline-block;
            width: shift(49);
            height: shift(24);
            margin-right: shift(10);
            margin-bottom: shift(-4);
        }
        &.icon-title {
            display: inline-block;
            width: shift(30);
            height: shift(30);
            margin-top: shift(-4);
            margin-left: shift(6);
            vertical-align: middle;
        }
        &.icon-title-local {
            display: inline-block;
            width: shift(56);
            height: shift(30);
            margin-top: shift(-4);
            margin-left: shift(6);
            vertical-align: middle;
        }
        &.icon-title-new {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/15/1460707810365-title-new-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-title-top {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/15/1460707810394-title-top-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-title-elite {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/15/1460707810386-title-elite-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-position {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/14/1460621908604-position-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-talkpop {
            width: shift(30);
            height: shift(28);
            background-image: url("https://s.momocdn.com/w/u/img/2016/07/05/1467715049996-comment-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-limit {
            margin-left: shift(-2);
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/29/1461911638370-limit-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-local {
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/29/1461911638355-local-icon.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-circleadmin {
            height: shift(24);
            width: shift(54);
            background-image: url("https://s.momocdn.com/w/u/img/2016/08/12/1470969542832-circle-admin.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-popular {
            height: shift(24);
            width: shift(54);
            background-image: url("https://s.momocdn.com/w/u/img/2016/07/13/1468388937548-popular.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-flooradmin {
            height: shift(24);
            width: shift(49);
            background-image: url("https://s.momocdn.com/w/u/img/2016/04/29/1461917353993-floor-admin.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-empty {
            width: shift(100);
            height: shift(118);
            background-image: url("https://s.momocdn.com/w/u/img/2016/06/30/1467256224856-icon-ghost.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-empty-blue {
            width: shift(100);
            height: shift(118);
            background-image: url("https://s.momocdn.com/w/u/img/2016/06/24/1466733648291-occupied.png?_bid=1090");
            background-size: 100% 100%;
            background-repeat: no-repeat;
        }
        &.icon-gender {
            position: relative;
            padding-left:shift(20);
            width: auto;
            height: shift(24);
            border-radius: shift(2);
            background-size: shift(16) shift(16);
            background-position: shift(5) center;
            background-repeat: no-repeat;
            &.icon-gender-boy {
                background-image: url(https://s.momocdn.com/w/u/img/2016/08/09/1470730194288-boy.png);
                background-color: #adc8f6;
            }
            &.icon-gender-girl {
                background-image: url(https://s.momocdn.com/w/u/img/2016/08/09/1470730194319-girl.png);
                background-color: #feb3c5;
            }
            > .age {
                display: table;
                height: shift(24);
                line-height: shift(24);
                width: shift(30);
                text-align: center;
                /*font-size: shift(18);*/
                font-size: 12px;
                transform: scale(0.75);
                color: #fff;
            }
        }
        &.icon-level {
            position: relative;
            width: shift(54);
            height: shift(24);
            border-radius: shift(2);
            background-size: shift(16) shift(16);
            background-position: shift(5) center;
            background-repeat: no-repeat;
            background-color: #c37a51;
            > .level {
                position: absolute;
                display: block;
                top: 50%;
                right: 0;
                left: 0;
                margin: 0 auto;
                height: shift(24);
                line-height: shift(24);
                text-align: center;
                /*font-size: shift(18);*/
                font-size: 12px;
                transform: translate(0, -50%) scale(0.75);
                color: #fff;
            }
        }
        &.icon-vip {
            width: auto;
            height: shift(24);
            > .vip {
                display: block;
                height: 100%;
                transform: scale(1.05)
            }
        }
        &.icon-circle-level{
            position: relative;
            height: shift(24);  
            width: auto;  
            border-radius: shift(2);
            background-color: #dcdcdc;
            > .circle-level {
                display: table;
                white-space: nowrap;
                height: shift(24);
                line-height: shift(24);
                text-align: center;
                /*font-size: shift(18);*/
                font-size: 12px;
                transform: scale(0.75);
                color: #fff;
            }      
        }
        &.icon-more{
            width: shift(46);
            height: shift(46);
            line-height: shift(46);
            text-align: center;
            > img{
                height: shift(35);
                vertical-align: middle;
            }
        }
        &.icon-like,&.icon-liked{
            width: shift(46);
            height: shift(49);
        }
        &.icon-comment{
            width: shift(46);
            height: shift(49);

        }
        &.icon-small-like{
            width: shift(30);
            height: shift(30);
            margin:0;
            padding:0;
            background-image: url(https://s.momocdn.com/w/u/img/custom/circle2/post/v1/like.png);
            background-size: auto 100%;
            background-position:cover;
            background-repeat:no-repeat;
        }
        &.icon-small-liked{
            width: shift(30);
            height: shift(30);
             margin:0;
            padding:0;
            background-image: url(https://s.momocdn.com/w/u/img/custom/circle2/post/v1/liked.png);
            background-size: auto 100%;
            background-position:cover;
            background-repeat:no-repeat;
        }
        &.icon-small-more{
            width: shift(30);
            height: shift(30);
            line-height: shift(30);
            text-align: center;
             margin:0 0 0 shift(20);
            padding:0;
            background-image: url(https://s.momocdn.com/w/u/img/custom/circle2/post/v1/more.png);
            background-size: auto 100%;
            background-position:cover;
            background-repeat:no-repeat;
        }
    }

    
    @keyframes rotate {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    }
</style>
<template>
    <div :class="iconClassObj" :style="iconStyleObj">
        <span class="age" v-if="type=='gender'" v-html="age"></span>
        <span class="level" v-if="type=='level'" :style="levelStyleObj">Lv.{{level}}</span>
        <img class="vip" v-if="type=='vip'" :src="imageUrl"></span>
        <span class="circle-level" v-if="type=='circle-level'" >{{level}}</span>
        <img :src="imageUrl" v-if="type == 'more'|| type == 'like' || type == 'comment' || type == 'liked'" >
    </div>
</template>

<script>

const LEVEL_OFFSET = 5;
const LEVEL_TONE = ['#eed7ca','#e3bea9','#d7a78c','#c37a51','#a45d34'];
const LEVEL_TONE_GAP = [0,10,20,30,40];
// https://s.momocdn.com/w/static/member_center/images/svip-year-4-1.1.png?_bid=1043
const VIP_IMAGES_URL = 'https://s.momocdn.com/w/static/member_center/images/';
const VIP_IMAGES_VERSION = '1.1';
const VIP_IMAGES_SEARCH = '?_bid=1043';

const COMMENT_IMAGE_URL = "https://s.momocdn.com/w/u/img/custom/circle2/post/v1/comment.png";
const LIKE_IMAGE_URL = "https://s.momocdn.com/w/u/img/custom/circle2/post/v1/like.png";
const LIKED_IMAGE_URL = "https://s.momocdn.com/w/u/img/custom/circle2/post/v1/liked.png";
const MORE_IMAGE_URL = "https://s.momocdn.com/w/u/img/custom/circle2/post/v1/more.png";

export default {
    props: {
        type:{},
        // 性别图标专属
        gender:{},
        age:{},
        // 陌陌等级、会员等级、圈子成员等级图标使用
        level:{},
        // 会员等级图标
        year:{},
        svip:{},
        isLike:{}
    },
    data:function () {
        var iconClassObj ={},
            iconStyleObj ={},
            levelStyleObj = {},
            imageUrl = '';


        iconClassObj.icon = true;
        iconClassObj['icon-'+ this.type] = true;
        
        switch(this.type){
            case 'gender':{
                this.gender == 'M' ? iconClassObj['icon-gender-boy'] = true : iconClassObj['icon-gender-girl'] = true;
                break;
            }
            case'level':{
                var bgc = '',
                    {level}=this;

                LEVEL_TONE_GAP.forEach(function (gap,index,arr){
                    if(level <= gap && arr[index-1]<level){
                        bgc = LEVEL_TONE[index -1];
                    }
                })
                levelStyleObj = {
                    right:this.level>9?`${LEVEL_OFFSET}px`:''
                };
                iconStyleObj ={
                    backgroundColor:bgc
                }
                break;
            }
            case 'circle-level':{
                iconStyleObj ={
                    backgroundColor:this.bgColor
                }
                break;
            }
            case 'vip':{
                var filename = '';
                filename += this.svip ? 'svip':'vip';
                filename += '-';
                filename += this.year ? 'year-':'';
                filename += this.level;
                filename += '-';                                              
                filename += VIP_IMAGES_VERSION + '.png';
                
                imageUrl = `${VIP_IMAGES_URL}${filename}${VIP_IMAGES_SEARCH}`;
                break;
            }
            case 'comment':{
                imageUrl = COMMENT_IMAGE_URL;
                break;
            }
            case 'like':{
                imageUrl = this.isLike ? LIKED_IMAGE_URL : LIKE_IMAGE_URL;
                break;
            }
            case 'more':{
                imageUrl = MORE_IMAGE_URL;
                break;
            }
        }
        return {
            iconStyleObj,
            levelStyleObj,
            iconClassObj,
            imageUrl,

        };
    },
    watch:{
        isLike(){
            this.imageUrl = this.isLike ? LIKED_IMAGE_URL : LIKE_IMAGE_URL;            
        }
    },
    methods:{
    }
}
</script>