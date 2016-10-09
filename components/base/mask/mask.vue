<style scoped lang="sass">
    .mask {
        position: fixed;
        background-color: rgba(0, 0, 0, 0.4);
        top: 0;
        left: 0;
        width: 100%;
        height: 101%;
        z-index: 5;
    }
</style>
<template>
    <div class="mask" @click="click">
        <slot></slot>
    </div>
</template>

<script>

export default {
    props: {
        show: {
            default: true
        }
    },
    methods:{
        click:function () {
            this.$emit('click');
        }
    }
}
</script>