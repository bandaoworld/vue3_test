<template>
    <h2>当前求和为：{{sum}}</h2>
    <button @click="sum++">点我+1</button>
    <hr>
    <h2>当前的信息为：{{msg}}</h2>
	<button @click="msg+='！'">修改信息</button>
    <hr>
	<h2>姓名：{{person.name}}</h2>
	<h2>年龄：{{person.age}}</h2>
	<h2>薪资：{{person.job.j1.salary}}K</h2>
    <button @click="person.name+='~'">修改姓名</button>
	<button @click="person.age++">增长年龄</button>
    <button @click="person.job.j1.salary++">涨薪</button>
</template>

<script>
    import { ref, watch,reactive} from 'vue'
export default {
    name: "Demo",
    setup() {
        //数据
        let sum = ref(0)
        let msg = ref('你好啊')
        let person = reactive({
            name:'张三',
			age:18,
			job:{
				j1:{
					salary:20
				}
			}
        })

        // 情况一：监视ref所定义的一个响应式数据
        // watch(sum, (newValue,oldValue)=>{
        //     console.log('sum的值变化了',newValue,oldValue)
        // }, {immediate: true})

        // 情况二：监视ref所定义的多个响应式数据
        // watch([sum, msg], (newValue,oldValue)=>{
        //     console.log('sum的值变化了',newValue,oldValue)
        // })

        // 情况三：监视reactive所定义的多个响应式数据的全部属性
        // 1. 注意无法获取正确的oldValue
        // 2. 强制开启了深度监视（deep配置无效）
        // watch(person, (newValue,oldValue)=>{
        //     console.log('person的值变化了',newValue,oldValue)
        // },{deep:true})  //deep配置无效

        // 情况四：监视reactive所定义的多个响应式数据的某个属性
        // watch(()=>person.age, (newValue,oldValue)=>{
        //     console.log('person的age的值变化了',newValue,oldValue)
        // })

        // 情况五：监视reactive所定义的多个响应式数据的某些属性
        // watch([()=>person.age, ()=>person.name], (newValue,oldValue)=>{
        //     console.log('person的age的值变化了',newValue,oldValue)
        // })

        // 特殊情况：
        watch(()=>person.job, (newValue,oldValue)=>{
            console.log('person的job的值变化了',newValue,oldValue)
        },{deep:true}) // 此处由于监视的是reactive所定义的对象钟的某个对象，所以deep有效 
        //返回一个对象（常用）
        return {
            sum,
            msg,
            person
        }
    },
};
</script>

<style>
    button{
        margin: 5px;
    }
</style>