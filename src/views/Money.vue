<template>
    <Layout class-prefix="layout">
        <NumberPad/>
        <Types/>
        <InputFrom/>
        <Tags :data-source="tags"  @update:data-source="tags  = $event"/>
    </Layout>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';
    import Layout from '@/components/Layout.vue';
    import Tags from '@/components/Money/Tags.vue';
    import InputFrom from '@/components/Money/InputFrom.vue';
    import Types from '@/components/Money/Types.vue';
    import NumberPad from '@/components/Money/NumberPad.vue';

    @Component({
        components: {NumberPad, Types, InputFrom, Tags, Layout}
    })
    export default class Money extends Vue {
        tags = ['衣','食','住','行']
    }
</script>
<style lang="scss">
    .layout-content{
        display: flex;
        flex-direction: column-reverse;
    }
</style>

<style scoped lang="scss">

</style>