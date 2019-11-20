<template>
  <div class="wrapper">
    <tab @switchTab="switchTab"></tab>
    <search></search>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
@Component({
  components: {
    tab: () => import("@/components/Tab.vue"),
    Search: () => import("@/components/Search.vue")
  }
})
export default class Punch extends Vue {
  switchTab(val: object, index: number) {
    console.log(val, index, "子组件触发出来的东西");
  }
}
</script>

<style scoped lang="scss">
.wrapper {
  .time {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    /*align-items: center;*/
    height: 94px;
    border-bottom: 1px #eee solid;
    .week {
      font-size: 30px;
      font-family: PingFangSC-Regular, PingFang SC;
      font-weight: 400;
      color: rgba(38, 38, 38, 1);
    }
    .date {
      padding-top: 10px;
      font-size: 14px;
      font-family: Helvetica;
      color: rgba(144, 144, 144, 1);
    }
  }
}
</style>
