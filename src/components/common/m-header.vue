<template>
    <header class="wrap">
        <i class="iconfont icon-left" @click="goBack"></i>
        <span>{{mTitle}}</span>
    </header>
</template>

<script>
    export default {
        components: {},
        props: {
            mTitle: {
                type: String,
                default: ''
            }
        },
        methods: {
            goBack() {
                this.$router.go(-1)
            }
        }
    }
</script>

<style lang="scss" type="text/scss" scoped>
    @import '../../common/style/mixin';

    header {
        position: relative;
        width: 100%;
        height: 120px;
        line-height: 120px;
        text-align: center;
        padding: 0 20px;
        font-size: 34px;
        border-bottom:3px #ededed solid;
        font-family:PingFang SC;
        font-weight: bold;
        @include boxSizing;
        .iconfont {
            position: absolute;
            left: 20px;
            top: 0;
            font-size: 50px;
            font-weight: bold;
        }
    }
</style>
