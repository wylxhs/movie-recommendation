<template>
    <div class="backtop"  @click="backTop">
        <img src="http://localhost:8080/data/backtop.png">
    </div>
</template>

<script>
    export default {
        methods: {
            isShow(){
                let toTop = document.querySelector('.backtop')
                let posY = window.pageYOffset || document.documentElement.scrollTop
                if(posY == 0){
                    toTop.style.display = "none"
                    // this.show = false
                }else{
                    toTop.style.display = "block"
                    // this.show = true
                }
            },
            backTop() {
                document.body.scrollTop = 0
                document.documentElement.scrollTop = 0
            }
        },
        mounted() {
            window.addEventListener("scroll", this.isShow);
        },
        destroyed() {
            window.removeEventListener("scroll", this.isShow);
        }
    }
</script>

<style lang="scss" scoped>
    .backtop{
        width: 1rem;
        height: 1rem;
        position: fixed;
        bottom: 1rem;
        right: .5rem;
        z-index: 99;
        display: none;
    }
    .backtop img{
        height: 100%;
        width: 100%;
    }
</style>
