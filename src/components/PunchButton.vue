<template>
  <div class="punchButtom">

    这里是打卡页面
    <span @click="add">{{message}}</span>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit } from "vue-property-decorator";
@Component
export default class PunchButton extends Vue {
  message: string = "zm";
  @Emit("clickadd")
  add() {
    return this.message;
  }
}
</script>

<style scoped lang="scss">
</style>
