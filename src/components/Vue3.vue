<template>
  <div>
    这里是预发版的vue3结合typeScript,这里使用的api和方法最终以vue3发布的为标准，这里只是基于现在的，具有时效性

    <div>要用typeScript写项目就要用 createComponent 包起来，这个感觉有点像react，steup 是vue3预发版的入口</div>
    <h1>这里是数据绑定{{count}}</h1>
    <div @click="increment">点击这里 count++</div>
    <div>{{plusOne}} computed 计算出来的值</div>
    <div>这里往下是vue2使用typeScript</div>
  </div>
</template>

<script lang="ts">
  import { ref, computed, watch, onMounted, Ref, createComponent ,components} from '@vue/composition-api'
  export default createComponent({
    setup(){
      let count: Ref<number> = ref(20)
      const plusOne:Ref<number> = computed(()=>count.value++)
      const increment = ()=>{
        return count.value++
      }
      watch(() => count.value * 2, val => {
        console.log(`count * 2 is ${val}`)
      })
      return {
        count,
        plusOne,
        increment
      }
    }
  })
</script>

<style scoped>

</style>
