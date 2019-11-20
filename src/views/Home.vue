<template>
  <div class="home">
    <div>
      <el-tabs v-model="activeName" @tab-click="handleClick">
        <el-tab-pane label="声明定义数据类型" name="first">
          <basic-data
            :parentD="forChildProp"
            @value-to-parent="mesgFormChild"
            ></basic-data>
        </el-tab-pane>
        <el-tab-pane label="对象练习" name="second">
          <obj-practice>

          </obj-practice>
        </el-tab-pane>
        <el-tab-pane label="接口练习" name="third">
          <interface-pro></interface-pro>
        </el-tab-pane>
        <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Watch, Prop, Emit } from "vue-property-decorator";
import HelloWorld from '@/components/HelloWorld.vue'
import BasicData from '@/views/basic/dataType.vue'
import Component from 'vue-class-component'
import ObjPractice from '@/views/basic/objectPractice.vue'
import InterfacePro from '@/views/basic/interfacePra.vue'
@Component ({
  components: {
    BasicData,
    ObjPractice,
    InterfacePro
  }
})
export default class Home extends Vue {
  activeName: string = 'first'
  forChildProp:string = '222'
  /**初始化 */
  created() {
    this.activeName = JSON.parse(localStorage.getItem('tableName')) || 'first'
  }

  /**methods */
  mesgFormChild(val) {
    console.log('子组件emit')
    this.forChildProp = val
  }

  handleClick(tab, event) {
    this.activeName = tab.name
    localStorage.setItem('tableName', JSON.stringify(tab.name))
  }
}
</script>
