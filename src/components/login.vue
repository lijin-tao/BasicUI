<script setup lang="ts">
import { onMounted, ref, toRef, toRefs, watch } from "vue";
import type { VbenFormSchema } from "../common";
import type { AuthenticationProps } from "../common/types";


interface Props extends AuthenticationProps{
    formSchema?:VbenFormSchema[];
}
interface TestProps{
  
  title:string;
  name?:string;
  age?:number;
  
}
defineOptions({
  name: "LoginComponent",
});
const props =withDefaults(defineProps<TestProps>(),{
  name:'test-name',
  age:18
});
const data=ref<TestProps>({...props});
const emits=defineEmits(['set-update']);
watch(()=>(data.value.title),(newvalues)=>{
  console.log("newvalues",newvalues);
  emits('set-update',newvalues);
});

function isShow(){
  console.log("我是login组件的方法");
}
defineExpose({
  isShow
})

</script>
<template>
    <div>Login Component

      <div><input type="text" class="input" v-model="data.title"></div>
      
      <button type="button" class="btn-test">保存</button>
      <button type="button" class="btn">测试</button>
    </div>

</template>

<style scoped lang="less">
@import '../assets/CSS/BasicStyle.less';
@test-color:#48bb5d;
.btn-color(test;@test-color);
.input-color(test;@test-color);

</style>