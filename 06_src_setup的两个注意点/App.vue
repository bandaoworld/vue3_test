<template>
    <Demo @hello="showHelloMsg" msg="你好啊" school="xupt">
        <template v-slot:qwe>
            <span>西邮</span>
        </template>
        <template v-slot:asd>
			<span>尚硅谷</span>
		</template>
    </Demo>
</template>

<script>
import Demo from "./components/Demo"
export default {
    name: "App",
    components:{Demo},
    setup(value) {
        function showHelloMsg(value){
            alert(`你好啊，你触发了hello事件，我收到的参数是:${value}！`)
        }
        return {
            showHelloMsg
        }
    },
    
};
</script>
