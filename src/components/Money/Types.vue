<template>
    <div>
        <ol class="types">
            <li :class="{selected: type === '-'}" @click="select('-')">支出</li>
            <li :class="{selected: type === '+'}" @click="select('+')">收入</li>
        </ol>
    </div>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';

    @Component
    export default class types extends Vue {
        type = '-'
        select(type:string){
            if(type !== '-' && type !== '+'){
                throw new Error('type is unknown')
            }
            this.type = type
        }
    }
</script>

<style scoped lang="scss">
    .types{
        background:#c4c4c4;
        display: flex;
        font-size: 24px;
        >li{
            width: 50%;
            height: 64px;
            display: flex;
            justify-content: center;
            align-items:center;
            position: relative;
            &.selected::after{
                content: '';
                position: absolute;
                left:0;
                bottom:0;
                width: 100%;
                height: 4px;
                background:#333;
            }
        }

    }
</style>