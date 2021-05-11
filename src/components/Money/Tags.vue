<template>
    <div class="tags">
        <ol class="current">
            <li>衣</li>
            <li>食</li>
            <li>住</li>
            <li>行</li>
        </ol>
        <div class="new">
            <button>新建标签</button>
        </div>
    </div>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';

    @Component
    export default class tags extends Vue {

    }
</script>

<style scoped lang="scss">
    .tags{
        font-size: 14px;
        padding: 16px;
        > .current{
            display: flex;
            > li{
                $h: 24px;
                background:#d9d9d9;
                height: $h;
                border-radius: $h/2;
                padding: 0 16px;
                line-height: $h;
                margin-right: 12px;
            }
        }
        > .new{
            padding-top: 16px;
            button{
                border: none;
                background: transparent;
                color: #999;
                border-bottom: 1px solid;
                padding: 0 6px;
            }
        }
    }
</style>