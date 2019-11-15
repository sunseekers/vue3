<template>
  <div id="app">
    <HelloWorld :msg="message" :age="age" @changeMsg="change"/>
  </div>
</template>

<script lang="ts">
  // https://www.npmjs.com/package/vue-property-decorator 使用方法
  // ts里面的装饰器  https://www.tslang.cn/docs/handbook/decorators.html
  // 初始化数据的时候，不用data，方法没有methods,更多的是用到了装饰器，@Component，@Prop,@Emit，值得注意的是@Component
  // 是放在export default 外面，其他的都是放在里面
  import { Component, Vue } from 'vue-property-decorator';
  import HelloWorld from './HelloWorld.vue';

  @Component({
    components: {
      HelloWorld,
    },
  })
  export default class Vue2 extends Vue {
    message:string ='Welcome to Your Vue2.js + TypeScript App 点击翻译 用到了子组件触发事件'
    age : number = 18
    change():string{
      this.message="这是vue2版本的TypeScript"
      return this.message
    }
  }
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>

