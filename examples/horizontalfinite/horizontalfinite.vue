<template>
    <div>
        <div class="scrollToIndex">
            <span>Scroll to index: </span>
            <input type="text" v-model.number.lazy="startIndex">
            <small>Change and blur to set start index.</small>
        </div>
        <VirtualList :size="50" :remain="8" :bench="44" class="list" :start="startIndex" scrolldirection="horizontal">
            <Item v-for="(udf, index) of items" :index="index" :key="index"></Item>
        </VirtualList>
        <div class="source">
            <a href="https://github.com/tangbc/vue-virtual-scroll-list/blob/master/examples/horizontalfinite/horizontalfinite.vue#L1">
                View this demo source code
            </a>
        </div>
    </div>
</template>

<script>
    import Item from './item.vue'
    import VirtualList from '../../index'

    export default {
        name: 'finite-test',

        components: { Item, VirtualList },

        data () {
            return {
                startIndex: 0,
                items: new Array(100000)
            }
        }
    }
</script>

<style>
    .scrollToIndex {
        padding-bottom: 20px;
    }
    input {
        outline: none;
        padding: .4em .5em;
        width: 55px;
        height: 16px;
        border-radius: 3px;
        border: 1px solid;
        border-color: #dddddd;
        font-size: 16px;
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
    }
    input:focus {
        border-color: #6495ed;
    }
    small {
        color: #999;
    }
    .list {
        background: #fff;
        border-radius: 3px;
        border: 1px solid #ddd;
        -webkit-overflow-scrolling: touch;
        overflow-scrolling: touch;
    }
    .source {
        text-align: center;
        padding-top: 20px;
    }
    .source a {
        color: #999;
        text-decoration: none;
        font-weight: 100;
    }
    @media (max-width: 640px) {
        small {
            display: none;
        }
    }
</style>

