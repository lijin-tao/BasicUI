<script setup lang="ts">
import { computed, onMounted, ref } from 'vue';
import { LoginComponent } from './components';
import type { VbenFormSchema } from './common';

const data= ref("dddd");
function updateData(newData:string){
  data.value=newData;
}
const child=ref<InstanceType<typeof LoginComponent>>();
onMounted(async()=>{
  await child.value!.isShow();
});
</script>

<template>
  <div>
    <p>{{ data }}</p>
    <LoginComponent ref="child"  :title="data" @set-update="updateData"/>
  </div>

</template>

<style scoped>

</style>
