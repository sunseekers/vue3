<template>
  <div class="hello">
    <h1 @click="changeMsg">{{ msg }}</h1>
    <div>初始化数据的时候，不用data，方法没有methods,更多的是用到了装饰器，@Component，@Prop,@Emit，值得注意的是@Component\n" +
      是放在export default 外面，其他的都是放在里面</div>
    <div> 我的名字叫{{name}}</div>
    <div> 你猜猜我现在多少岁了 ？？ {{age}}</div>
    <div @click="changeCount">{{count}} count不断++ </div>

  </div>
</template>

<script lang="ts">
import { Component, Prop,Emit, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  @Prop() private age!: number;

  count:number=0
  name:string = 'sunseekers'
  changeCount ():number{
    this.count ++
    return this.count
  }

  @Emit("changeMsg")
  changeMsg():void{
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
