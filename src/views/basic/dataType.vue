<template>
  <div class="body-container">
    <p style="color: red">这个是初始的姓名: {{name}}</p>
    <div>
      <p v-for="item in options" :key="item.value" @click="btnClick(item)">{{item.label}}</p>
    </div>
    <p style="color: blue">这个是根据计算属性得到的: {{numberTest}}</p>
    <p>this name is for Parent {{parentD}}</p>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { Watch, Prop, Emit } from "vue-property-decorator";
@Component({
  components: {}
})

// interface Item {
//   value: string,
//   label: string
// }
export default class DataType extends Vue {
  /**props */
  @Prop({default: '111'})
  parentD: [string, number]

  /** data */
  name: string = "张天";
  query: object = {
    name: "ssss",
    age: 333333
  };
  options: object = [
    { value: "1", label: "啊说不定你就阿三" },
    { value: "2", label: "阿拉山口的" },
    { value: "3", label: "喔 i 记得送" }
  ];
  /**watch */
  @Watch("name")
  onNameChange(val: string, oldVal: string) {
    this.valueToParent(val)
  }

  /**emit */
  @Emit()
  valueToParent(val) {
    return val
  }
  /**computed */
  get numberTest():string {
    return this.name + 'sss'
  }
  /**methods */
  btnClick(val: any): void {
    console.log(val);
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