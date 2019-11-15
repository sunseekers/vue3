<template>
<div class="punchButtom">
  这里是打卡页面
</div>
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  import HelloWorld from './HelloWorld.vue';

  @Component({
    components: {
      HelloWorld,
    },
  })
  export default class PunchButton extends Vue {
    name: "PunchButton.vue"
    message:string ='Welcome to Your Vue2.js + TypeScript App 点击翻译 用到了子组件触发事件'

    created(): void {
      console.log(Component)

    }
  }
</script>

<style scoped lang="scss">

</style>
