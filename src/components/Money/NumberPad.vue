<template>
    <div class="numberPad">
        <div class="output">{{output}}</div>
        <div class="buttons">
            <button @click="inputContent">1</button>
            <button @click="inputContent">2</button>
            <button @click="inputContent">3</button>
            <button @click="cutout">删除</button>
            <button @click="inputContent">5</button>
            <button @click="inputContent">6</button>
            <button @click="inputContent">7</button>
            <button @click="clear">清空</button>
            <button @click="inputContent">8</button>
            <button @click="inputContent">9</button>
            <button @click="inputContent">10</button>
            <button class="ok">OK</button>
            <button @click="inputContent">0</button>
            <button @click="inputContent" class="zero">.</button>
        </div>
    </div>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';

    @Component
    export default class NumberPad extends Vue {
        output = '0'
        inputContent(event:MouseEvent) {
            const button = event.target as HTMLButtonElement
            const input = button.textContent! //  强制指定类型 ！= as string
            if(this.output === '0'){
              if('0123456789'.indexOf(input)>=0){
                  this.output = input
              }else{
                  this.output += input
              }
              return
            }
            if(this.output.indexOf('.')>=0){
                if(input === '.'){
                    return;
                }
            }
            this.output += input
        }
        cutout(){
            if(this.output.length === 1){
                this.output = '0'
            }else{
                this.output = this.output.slice(0,-1)
            }
        }
        clear(){
            this.output = '0'
        }
    }
</script>

<style scoped lang="scss">

    .numberPad {
        @import '~@/assets/styles/helper.scss';
        .output {
            font-size: 36px;
            font-family: Consolas, monospace;
            padding: 9px 16px;
            text-align: right;
            @extend %output-shadow;
        }
        .buttons {
            @extend %clearFix;
            button {
                background: transparent;
                border: none;
                width: 25%;
                height: 64px;
                float: left;
                &.ok {
                    float: right;
                    height: 64*2px;
                }

                &.zero {
                    width: 25*2%;
                }

                $bg: #f2f2f2;

                &:nth-child(1) {
                    background: $bg;
                }

                &:nth-child(2), &:nth-child(5) {
                    background: darken($bg, 4%);
                }

                &:nth-child(3), &:nth-child(6), &:nth-child(9) {
                    background: darken($bg, 4*2%);
                }
                &:nth-child(4), &:nth-child(7), &:nth-child(10),&:nth-child(13) {
                    background: darken($bg, 4*3%);
                }
                &:nth-child(8), &:nth-child(11) {
                    background: darken($bg, 4*4%);
                }
                &:nth-child(14){
                    background: darken($bg, 4*4.5%);
                }
                &:nth-child(12){
                    background: darken($bg, 4*5%);
                }
            }
        }

    }
</style>