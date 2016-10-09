<style scoped lang="sass">
    @import "../../../style/scss/variable";
    @import "../../../style/scss/mixin";
    @import "../../../style/scss/component";

    $primary-bgc:#3462ff;
    $primary-color:#fff;
    $gray-bgc:#f0f0f0;
    $gray-color:#5a5a5a;
    
    .button{
        display: inline-block;
        padding:shift(26) 0;
        font-size:shift(32);
        line-height:shift(36);
        text-align: center;
        border-radius: shift(5);
        appearance: none;
    }

    .button-block{
        display: block;
    }
    .button-primary{
        background-color: $primary-bgc;
        color: $primary-color;
    }
    .button-gray{
        background-color: $gray-bgc;
        color: $gray-color;
    }
</style>
<template>
    <a :class="btnClassObj" :href="href">
        <slot></slot>
    </a>
</template>

<script>

export default {
    props: {
        show: {
            default: true
        },
        href:{
            default:'javascript:'
        },
        block:{
            default:false
        },
        stress:{
            default:'primary'
        }
    },
    data:function (){
        return {
            btnClassObj:{
                'button':true,
                'button-block':this.block,
                'button-primary':this.stress=='primary',
                'button-gray':this.stress=='gray',
                
            }
        }
    },
    created:function () {
    },
    methods:{
        click:function () {
            this.$emit('click');
        }
    }
}
</script>