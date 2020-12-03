<template>
    <div class="sort">
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.listSort" :key="index" @click="selectType(item.SortIndex)">
                {{item.sortType}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.areaSort" :key="index" @click="selectType('area')">
                {{item}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.typeSort" :key="index" @click="selectType('type')">
                {{item}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.yearSort" :key="index" @click="selectType('year')">
                {{item}}
            </li>
        </ul>
        <ul>
            <li class="sort_item" v-for="(item, index) in sortMsg.methodSort" :key="index" @click="selectType('year')">
                {{item}}
            </li>
        </ul>
    </div>
</template>

<script>
    import { mapMutations } from "vuex"
    export default {
        props: {
            sortMsg: Object
        },
        data(){
            return {

            }
        },
        methods: {
            selectType(item){
                this.selectSort(item)
                
            },
            ...mapMutations(['selectSort'])
        },
        
    }
</script>

<style lang="scss" scoped>
    
        .sort ul{
            height: 0;
            padding-bottom: .7rem;
            overflow-x: scroll;
            overflow-y: hidden;
            white-space: nowrap;
        }
            .sort_item{
                display: inline-block;
                padding:3px 5px;
                margin: 0 5px;
            }
            .sort_item_active{
                background: #ccc;
                border-radius: .3rem;                
            }
</style>
