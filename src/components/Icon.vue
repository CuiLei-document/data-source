<template>
    <div>
        <svg class="icon">
            <use :xlink:href="`#` + name"></use>
        </svg>
    </div>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component, Prop} from 'vue-property-decorator';
     let importAll = (requireContent:__WebpackModuleApi.RequireContext) =>requireContent.keys().forEach(requireContent)
    try{
         importAll(require.context('../assets/icons',true,/\.svg$/))
    }catch (err) {
        console.log(err);
    }
    @Component
    export default class Icon extends Vue {
    @Prop(String) name!:string
    }
</script>

<style scoped lang="scss">
    .icon {
        width: 2em; height: 2em;
        vertical-align: -0.15em;
        fill: currentColor;
        overflow: hidden;
    }
</style>