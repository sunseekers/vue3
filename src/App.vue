<template>
  <div>
    {{ count }} {{ object.foo }}
    <button @click="increaseCapacity()">
      点击 count ++
    </button>
    <div>count 的两倍{{object.double}}</div>
  </div>
</template>

<script>
  import { ref, reactive,computed } from '@vue/composition-api'

  export default {
    setup() {
      // ref使用
      const count = ref(10)
      // reactive，computed 使用
      const object = reactive({
        count: 11,
        double: computed(() => count.value *23)
    })
      // 方法
      function increaseCapacity() {
        count.value++
      }
      // 返回的对象里面的东西会暴露给`template`直接使用
      return {
        count,
        object,
        increaseCapacity
      }
    }
  }
</script>
