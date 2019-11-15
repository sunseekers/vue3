<template>
<div class="wrapper">
  <div class="time">
    <span class="week">星期五</span>
    <span class="date">2018年5月15日</span>
    <punch-button></punch-button>
  </div>
</div>
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  @Component({
    components:{
      PunchButton:()=>import("@/components/PunchButton")
  }
  })
  export default {
    name: "Punch.vue",
    created(): void {
      console.log(Component)

    }
  }
</script>

<style scoped lang="scss">
.wrapper{
  padding: 15px;
  .time{
    display: flex;
    flex-direction: column;
    justify-content:flex-start;
    /*align-items: center;*/
    height:94px;
    border-bottom: 1px #eee solid;
    .week{
      font-size:30px;
      font-family:PingFangSC-Regular,PingFang SC;
      font-weight:400;
      color:rgba(38,38,38,1);
    }
    .date{
      padding-top:10px;
      font-size:14px;
      font-family:Helvetica;
      color:rgba(144,144,144,1);
    }
  }
}
</style>
