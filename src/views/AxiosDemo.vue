<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
    </div>
</template>

<script>
    /*
    * 请求方法
    *
    * get：获取数据
    * post：提交数据
    * put：更新数据(所有数据推送到后端)
    * patch：更新数据(修改的数据推送到后端)
    *delete：删除数据
    *
    * */
    import Axios from 'axios'
    export default {
        name: "AxiosDemo",
        created() {
            Axios.get('/data.json',{
                params:{
                    id: 1
                }
            }).then((res) => {
                console.log(res)
            })
            Axios({
                method: 'get',
                url: '/data.json',
                params:{
                    id:12
                }
            }).then(res=>{
                console.log(res)
            })
            //application/json
            let data={
                id: 111
            }
            Axios.post('/post',data).then(res=>{
                console.log(res)
            })
            Axios({
                method: 'post',
                url: '/data',
                data: data
            }).then(res=>{
                console.log(res)
            })
            //form-data,表单提交图片，文件
            let formData = new FormData()
            for (let key in data){
                formData.append(key,data[key])
            }
            Axios.post('/post',formData).then(res=>{
                console.log(res)
            })
            //更新 提交的所有
            Axios.put('/put',data).then(res=>{
                console.log(res)
            })
            //部分更新
            Axios.patch('/patch',data).then(res=>{
                console.log(res)
            })
            // 参数在url后面
            Axios.delete('/data', {
                params: {
                    id: 123
                }
            }).then(res=>{
                console.log(res)
            })
            //参数在请求体里面
            Axios.delete('/data', {
                data: {
                    id: 123
                }
            }).then(res=>{
                console.log(res)
            })
            Axios({
                method: 'delete',
                url: '/data',
                params: {
                    id: 123131
                }
            }).then(res=>{
                console.log(res)
            })


        }
    }
</script>

<style scoped>

</style>