<template>
  <!-- tab 切换 -->
  <div class="tab">
    <div v-for="(item, index) in tab" :key="`tab${index}`" :class="{ currentColor: currentIndex === index }" @click="switchTab(item, index)">
      {{ item.label }}
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit, Prop } from "vue-property-decorator";
@Component
export default class Tab extends Vue {
  currentIndex: number = 0;
  @Prop({
    default: () => {
      return [
        {
          label: "申请中",
          value: 0
        },
        {
          label: "通 过",
          value: 1
        },
        {
          label: "不通过",
          value: 2
        }
      ];
    }
  })
  tab!: Array<object>;
  @Emit("switchTab")
  switchTab(item: Array<number>, index: number) {
    this.currentIndex = index;
  }
}
</script>

<style scoped lang="scss">
.tab {
  background-color: #ffffff;
  line-height: 46px;
  font-size: 18px;
  font-weight: 500;
  color: rgba(51, 51, 51, 1);
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: relative;
  .currentColor {
    color: rgba(55, 202, 124, 1);
    border-bottom: 3px solid;
  }
}
</style>
