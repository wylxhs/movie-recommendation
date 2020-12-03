<template>
    <div class="list">
        <HeadTop head-title="电影列表" go-back="true" ></HeadTop>
        <MovieSort :sortMsg = "sortMsg"></MovieSort>
        <MovieBrief :movieList = "movieList"></MovieBrief>
    </div>
</template>

<script>
    import HeadTop from '@/components/header/Head'
    import MovieSort from './pages/MovieSort'
    import MovieBrief from './pages/MovieBrief'
    import {mapState} from 'vuex'
    export default {
        name: "List",
        data(){
            return {
                sortMsg:{
                    listSort:[
                        {
                            sortType:"推时间",
                            SortIndex:"year"
                        },
                        {
                            sortType:"推评分",
                            SortIndex:"score"
                        },
                        {
                            sortType:"喜欢数",
                            SortIndex:"like"
                        },
                        {
                            sortType:"新上线",
                            SortIndex:"year"
                        }
                    ],
                    areaSort:['全部地区', '华语', '港台', '日韩', '东南亚', '美国', '其它'],
                    typeSort:['全部类型', '喜剧', '爱情', '动作', '恐怖', '动画', '其它'],
                    yearSort:['全部年份', '2020-2010', '2009-2000', '1999-1990', '1989-1980','其它'],
                    methodSort:['全部方式', '可跳转', '下载链接', '仅推荐']
                },
                movieList:[]
            }
        },
        components:{
            HeadTop,
            MovieSort,
            MovieBrief
        },
        methods:{
            Sort(sortClass){
                this.movieList.sort((a, b) => {                    
                    return b[sortClass]-a[sortClass]
                })
                // console.log(this.movieList)
            } 
        },
        mounted(){
            this.axios.get("http://localhost:8080/data/movie.json")
                .then((res) => {
                    this.movieList = res.data.movieList
                    // this.Sort(this.$store.state.sortType)
                    this.Sort(this.$store.state.sortType)
                    // console.log(this.movieList)
                })
        },
        computed: {
            ...mapState(['sortType'])
        }
    }
</script>

<style>
    .list{
        background: #fff;
    }
</style>
