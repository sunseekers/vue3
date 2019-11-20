<template>
  <div class="selectDrop">
    <div class="select">
      <div @click="toggleDrop(item,index)" v-for="(item,index) in list.title" :key="index">
        <span>{{item.label}}</span>
        <i :style="{transform:`rotate(${showIndex === index?'180deg':'0deg'})`}" class="iconfont">&#xe6a1;</i>
      </div>
    </div>

    <div class="dropContent" :style="{maxHeight:`${showDrop?200+'px':0}`,visibility:`${showDrop?'visible':'hidden'}`}" :class="showDrop?'activeClass':''">
      <div :style="{color:`${orange(item)?'#FB7F33':''}`}" @click="selectItem(item,showIndex)" class="item" v-for="(item,index) in list.select[showIndex]" :key="index">
        {{item.label}}
        <span v-if="orange(item)" class="iconfont gou">&#xe604;</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";

@Component({
  props: {
    list: {
      type: Object,
      default: () => {}
    }
  }
})
export default class PunchButton extends Vue {
  @Prop({
    default: () => {
      return {
        title: [
          { label: "全部模版", value: 1 },
          { label: "全部学科", value: 2 },
          { label: "全部类型", value: 3 },
          { label: "全部年级", value: 4 }
        ],
        select: [
          [
            { label: "全部模版", value: 1 },
            { label: "推荐模版", value: 2 },
            { label: "我的模板", value: 2 }
          ],
          [
            { label: "全部学科", value: 1 },
            { label: "语文", value: 2 },
            { label: "数学", value: 2 }
          ],
          [
            { label: "全部类型", value: 1 },
            { label: "全部类型1", value: 2 },
            { label: "全部类型2", value: 2 }
          ],
          [
            { label: "全部年级", value: 1 },
            { label: "一年级", value: 2 },
            { label: "二年级", value: 2 }
          ]
        ]
      };
    }
  })
  list!: Object;
  showIndex: number = -1;
  showDrop: boolean = false;
  currentIndex: number = 0;
  toggleDrop(item: Object, index: number) {
    if (this.showIndex === index) {
      this.showIndex = -1;
      this.showDrop = false;
    } else {
      this.showIndex = index;
      this.showDrop = true;
    }
  }
  selectItem(item: Array<number>, index: number) {
    this.showDrop = false;
    this.currentIndex = index;
    this.list.title[this.showIndex] = item;
    this.showIndex = -1;
  }
  orange(item: Array<number>) {
    return this.list.title[this.showIndex].label === item.label;
  }
}
</script>

<style scoped lang="scss">
.selectDrop {
  padding: 0 15px;

  .select {
    width: 100%;
    line-height: 36px;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #ebebeb;
    i {
      display: inline-block;
      transition: all 0.5s;
    }
  }
  .dropContent {
    z-index: 100;
    width: 100%;
    // max-height: 0;
    overflow-y: scroll;
    background: #fff;
    position: absolute;
    top: 36px;
    left: 0;
    padding: 0 15px;
    .item {
      width: 100%;
      height: 40px;
      line-height: 40px;
      padding: 0 15px;
      text-align: left;
      background: #fff;
      font-size: 14px;
      font-family: PingFangSC;
      font-weight: 400;
      color: rgba(51, 51, 51, 1);
      position: relative;
      border-bottom: 1px solid #ebebeb;
    }
    .gou {
      position: absolute;
      right: 15px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 12px;
      line-height: 40px;
      font-weight: 500;
    }
  }
}
</style>
