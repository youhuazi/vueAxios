<template>
    <div>123456</div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "AsyncAwait",
        created() {
        //    axios.all() 参数表示的是一个一个请求
            // axios.spread()，返回的是并发的结果
            axios.all([
                axios.get('/data.json'),
                axios.get('/city.json')
            ]).then(
                axios.spread((dataRes,CityRes)=>{
                    console.log(dataRes, CityRes)
                })
            )
            let result = this.doubleAfter2Seconds()
            console.log(result)
        },
        methods: {
            async AsyncAwait() {
                return 'hello world'
            },
            doubleAfter2Seconds(num){
                return setTimeout({
                    num: num*2
                },2000)
            }

        }
    }
</script>

<style scoped>

</style>