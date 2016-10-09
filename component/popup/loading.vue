<style scoped lang="sass">

@function shift($size) {
    @return $size/32+rem;
}

.loading{
    width: shift(64);
    height: shift(64);
    background-image: url("https://s.momocdn.com/w/u/img/03/10/1457603892170-ic_loading.png?_bid=1090");
    background-size:100%;
    animation: rotate-loading 1s ease-in-out infinite;
}
.loading-fixed{
    position: fixed;
    left: 50%;
    top: 50%;
    text-align: center;
    /*transform:translate(-50%,-50%);*/
    margin-top: - shift(32);
    margin-left: - shift(32);
    z-index: 101;
}

@keyframes rotate-loading {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
}
</style>
<template>
    <div v-bind:class="classObject" v-show="show"></div>
</template>

<script>

export default {
    props: {
        show:{
            default: true,
            twoWay:true
        },
        isFixed:{
            default:false
        }
    },
    computed:{
        classObject:function (){
            return {
                'loading':true,
                'loading-fixed':this.isFixed
            }
        }
    }
}

</script>