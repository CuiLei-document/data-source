<template>
    <div class="layout-wrapper">
        <div class="content" :class="classPrefix && `${classPrefix}-content`" >
        <slot/>
        </div>
        <Nav></Nav>
    </div>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component, Prop} from 'vue-property-decorator';
    import Nav from '@/components/Nav.vue';
    @Component({
        components: {Nav}
    })
    export default class Layout extends Vue {
    @Prop(String) classPrefix!: string;
    }
</script>

<style scoped lang="scss">
.layout-wrapper{
    border: 1px solid red;
    display: flex;
    flex-direction: column;
    height: 100vh;
    > .content{
        flex-grow: 1;
        overflow: auto;
    }
}
</style>