<template>
    <div class="tags">
        <ol class="current">
            <li v-for="tag in dataSource" :key="tag" :class="{selected: selectTags.indexOf(tag)>=0}" @click="selected(tag)">
                {{tag}}
            </li>
        </ol>
        <div class="new">
            <button @click="newTag">新建标签</button>
        </div>
    </div>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component, Prop} from 'vue-property-decorator';

    @Component
    export default class tags extends Vue {
        @Prop({required: true}) dataSource!:string[]
        selectTags: string[] = []
        selected(tag:string){
            const index = this.selectTags.indexOf(tag)
            if(index>=0){
                this.selectTags.splice(index,1)
            }else{
                this.selectTags.push(tag)
            }
        }
        newTag(){
            const name = window.prompt('请输入标签名')
            if(name === ''){
                window.alert('标签名不能为空')
            }else{
                this.$emit('update:dataSource',[...this.dataSource,name])
            }
        }
    }
</script>

<style scoped lang="scss">
    .tags {
        font-size: 14px;
        padding: 16px;

        > .current {
            display: flex;
            flex-wrap: wrap;

            > li {
                $h: 24px;
                background: #d9d9d9;
                height: $h;
                border-radius: $h/2;
                padding: 0 16px;
                line-height: $h;
                margin-right: 12px;
                margin-top: 6px;
                &.selected{
                    background: #c4c4c4;
                    color: white;
                }
            }
        }

        > .new {
            padding-top: 16px;

            button {
                border: none;
                background: transparent;
                color: #999;
                border-bottom: 1px solid;
                padding: 0 6px;
            }
        }
    }
</style>