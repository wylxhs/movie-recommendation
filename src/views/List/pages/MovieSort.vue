<template>
    <div class="sort">
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.listSort" :key="'list'+index" @click="emitList(item.SortIndex)">
                {{item.sortType}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.areaSort" :key="'area'+index" @click="selectType('area')">
                {{item}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.typeSort" :key="'type'+index" @click="selectType('type')">
                {{item}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.yearSort" :key="'year'+index" @click="selectType('year')">
                {{item}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.methodSort" :key="'year1'+index" @click="selectType('year')">
                {{item}}
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        props: {
            sortMsg: Object
        },
        methods: {
            emitList(sortI){
                this.$emit('click-item', sortI)
            }
        }
        
    }
</script>

<style lang="scss" scoped>
    .sort{
        border-top: 1px #333 solid;
    }
        .sort ul{
            height: 0;
            padding-bottom: .7rem;
            overflow-x: scroll;
            overflow-y: hidden;
            white-space: nowrap;
        }
            .sort_item{
                display: inline-block;
                padding:3px 15px;
                margin: 0 5px;
            }
            .sort_item_active{
                background: rgb(236, 235, 235);
                border-radius: .3rem;  
                color: rgb(245, 129, 51);              
            }
</style>
