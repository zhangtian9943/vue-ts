<template>
  <div class="body-container">
    <p>{{name}}</p>
    <div>
      <p v-for="item in options" :key="item.value" @click="btnClick(item)">{{item.label}}</p>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { Watch } from "vue-property-decorator";
import home from "../Home.vue"

class Item {
  value: string = '22';
  label: number = 22;
  private cc :string = 'sjanda'
  static cale(val):void {
    console.log(val, '/////2222wwee//////')
  } 
}
class child extends Item {
  static parentName(val) {
    console.log(super.cale(val))
  }
}
@Component({
  components: {}
})
export default class ObjPractice extends Vue {
  /** data */
  name: string = "张天";
  query: {} = {
    name: "ssss",
    age: 333333
  };
  // numberArr: number[][] = [[1, 2, 3], [23, 24, 25]]
  options: {} = [
    { value: "1", label: "啊说不定你就阿三" },
    { value: "2", label: "阿拉山口的" },
    { value: "3", label: "喔 i 记得送" }
  ];
  /**watch */
  @Watch("name")
  onNameChange(val: string, oldVal: string) {
    console.log(val, oldVal, "change扩散的看书的");
  }
  /**methods */
  btnClick(val: any): void {
    // const aa = new Item()
    Item.cale('334455')
    // const  aa = new child()
    console.log(child.parentName('ss'), '在这个人')
    console.log(val);
    console.log(typeof val)
    this.name = val.label;
  }
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