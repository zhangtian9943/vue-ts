<template>
  <div class="body-container">
    <div>
      <p v-for="item in options" :key="item.value" @click="btnClick()">{{item.label}}</p>
    </div>
    <p style="color: red">测试：{{ttset}}</p>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { Watch } from "vue-property-decorator";
interface Columns {
  [propName: string]: any
}

@Component({
  components: {}
})
export default class ObjPractice extends Vue {
  /** data */
 
  
  options: Columns[] = [
    { value: "1", label: "啊说不定你就阿三" },
    { value: "2", label: "阿拉山口的" },
    { value: "3", label: "喔 i 记得送" }
  ];

  rows: Columns = {
    list: {
      id: 'name',
      age: 22
    },
    pageTotal: 400,
    doThis: ['1', '2', '3']

  }
  ttset: string = ''
  /**watch */
 
  /**methods */
  // btnClick(item: Columns = {label: 1}): void {  //w为什么改变了ttest的数据类型却
  //   console.log(this.rows.list.id, typeof this.ttset)
  //   this.ttset = item.label
  //   console.log(typeof this.ttset, typeof item.label, item.label, '//////')
  //   console.log(this.ttset)
  // }
}
</script>
<style>
.body-container {
  text-align: left;
  padding: 0 21px;
}
</style>
<style lang="scss" scoped>
</style>