<template>
    <nav>
        <router-link to="/money" class="item" active-class="selected">
            <Icon name="money" class="icon"/>
           <span>记账</span>
        </router-link>
        <router-link to="/labels" class="item" active-class="selected">
          <Icon name="Label" class="icon"/>
             <span>标签</span>
        </router-link>
        <router-link to="/statistics" class="item" active-class="selected">
            <Icon name="statistics" class="icon"/>
            <span>统计</span>
        </router-link>
    </nav>
</template>

<script lang='ts'>
    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';
   import x from '@/assets/icons/money.svg'
    import Icon from '@/components/Icon.vue';

    console.log(x);
    @Component({
        components: {Icon}
    })
    export default class Nav extends Vue {

    }
</script>

<style scoped lang="scss">
    @import '~@/assets/styles/helper.scss';
nav{
    @extend %nav-shadow;
    display: flex;

    > .item{
        width: 33.33333%;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 5px;
        .icon{
            width: 32px;
            height: 32px;
        }
    }
    > .item.selected{
        color:red;
    }

}
</style>