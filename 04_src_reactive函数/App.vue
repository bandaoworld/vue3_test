<template>
    <h1>一个人的信息</h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <h3>工作种类：{{ person.job.type }}</h3>
    <h3>工作薪水：{{ person.job.salary }}</h3>
    <h3>爱好：{{ person.hobby }}</h3>
    <h3>测试的数据c：{{ person.job.a.b.c }}</h3>
    <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import { reactive } from 'vue'
export default {
    name: "App",
    setup() {
        //数据
        let person = reactive({
            name: 'bandao233',
            salary: '30k',
            job: {
                type: '前端工程师',
                salary: '30K',
                a: {
                    b: {
                        c: 666
                    }
                }
            },
            hobby: ['抽烟', '喝酒', '烫头']
        })

        //方法
        function changeInfo() {
            person.name = 'bandao'
            person.age = 20
            person.job.type = 'UI设计师'
            person.job.salary = '60K'
            person.job.a.b.c = 99
            person.hobby[0] = '学习'
        }

        //返回一个对象（常用）
        return {
            person,
            changeInfo,
        }
    },
};
</script>
