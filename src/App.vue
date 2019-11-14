<template>
  <div>
    {{ count }} {{ object.name }}
    <button @click="increaseCapacity()">
      点击 count ++{{plusOne}}
    </button>
    <div>count 的23倍{{object.double}}</div>
  </div>
</template>

<script>
  import { ref,reactive,computed,watch,onMounted,onUpdated,onUnmounted,onBeforeMount } from '@vue/composition-api'
  export default {
    // setup 是 Composition API 的入口，也就是 vue组件的入口
    // setup 一个对象，里面可以有函数，状态，等等，可以直接在页面中使用
    // setup 的第一个参数就是props，第二个参数是上下文
    // setup  里面的 this 不可用
    // props 生命周期在 setup  前面，可以看控制台的输出


    // 这两个等会测试,不知道有什么用
    // isRef 检查这个只是不是引用类型的
    // toRefs 把不是引用类型的转化为引用类型

    // createComponent 页面代码使用ts书写

    // computed 和以前一样，可以单独放在外面用，也可以放到 reactive里面,依旧有get和set
    props:{
      name:{
        type:String,
        default:"sunseekers"
      }
    },
    setup(props,context) {
      console.log(props.name,'props 最先执行')
      console.log(context,'step 第二个参数是上下文')
      watch(()=>{
        console.log(props.name,'props 发生变化的时候watch,初始化的时候会执行')

      })
      // ref使用
      const count = ref(10)
      // reactive，computed 使用
      const object = reactive({
        name: 'sunseekers',
        double: computed(() => count.value *23),
    })

      const plusOne = computed(() => count.value + 1)

      console.log(object,'reactive 创建的类似于原来的data')
      // 方法 类似于原来的methods
      function increaseCapacity() {
        count.value++
      }
      console.log()
       // 生命周期
      onBeforeMount(()=>{
        console.log('onBeforeMount!')

      })
      onMounted(() => {
        console.log('mounted!')
      })
      onUpdated(() => {
        console.log('updated!')
      })
      onUnmounted(() => {
        console.log('unmounted!')
      })
      console.log('setup')
      // 返回的对象里面的东西会暴露给`template`直接使用
      // components: {
      //   SelectItem,
      //     HolidayItem,
      //     Multimedia,
      //     CourseItem,
      //     FooterItem,
      //     DocumentItem,
      //     ImageItem,
      //     VacateTime
      // },
      return {
        count,
        object,
        plusOne,
        increaseCapacity
      }
    }
  }
</script>
