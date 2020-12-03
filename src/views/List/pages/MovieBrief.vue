<template>
    <div class="brief">
        <ul>
            <li class="brief_item" v-for="(item, index) in movieList" :key="'item'+index">
                <div class="b_img">
                    <img :src="item.imgUrl" alt="">
                </div>
                <div class="b_text">
                    <div class="b_title">
                        {{item.title}}
                    </div>
                    <div class="score_like">
                        <span class="b_score">
                            {{item.score}}
                        </span>
                        <span class="b_like">
                            {{item.like}}
                        </span>
                    </div>
                    <div class="year_area">
                        <span class="b_year">
                            {{item.year}}
                        </span>
                        <span class="b_area">
                            {{item.area}}
                        </span>
                        <span class="b_type">
                            {{item.type}}
                        </span>
                    </div>
                    <div class="author">
                        <span class="b_director" v-for="(director, index1) in item.director" :key="'director'+index1">
                            {{director}} 
                        </span>/
                        <span class="b_author" v-for="(author, index2) in item.author" :key="'author'+index2">
                            {{author}}
                        </span>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        props: {
            movieList: Array
        }
    }
</script>

<style lang="scss" scoped>
    .brief_item{
        margin: 8px;
        overflow: hidden;
    }
        .b_img{
            height: 140px;
            width: 100px;
            float: left;
        }
        .b_img img{
        height: 140px;
            width: 100px;
        }
        .b_text{
            display: inline-block;
            padding: 10px;
            width: 239px;
        }
            .b_title{
                overflow:hidden;
                text-overflow:ellipsis;
                display:-webkit-box;
                -webkit-box-orient:vertical;
                -webkit-line-clamp:2; 
            }
</style>
