<template>
  <div id="appindex">
    <button @click="visible = !visible">显示/隐藏标尺</button>
    <button @click="presetLine = []">清空</button>
    <button @click="presetLine = [{ type: 'h', site: 300 }, { type: 'v', site: 200 }]">修改</button>
    <section style="margin: 50px;padding: 50px;border: 1px solid red;height: 600px;">
      <vue3-ruler-tool
        :value="presetLine"
        :step-length="50"
        :parent="true"
        :is-scale-revise="true"
        :visible.sync="visible"
        @input="input"
      >
        <img
          src="https://cn.vuejs.org/images/logo.png"
          style="width: 300px;height: 300px;margin: 100px;"
          alt
        />
        <!-- <iframe src="https://www.baidu.com" width="500" height="300" /> -->
      </vue3-ruler-tool>
    </section>
  </div>
</template>
<script lang="ts">
import { defineComponent, reactive, ref } from 'vue'
import Vue3RulerTool from './components/vue3-ruler-tool.vue'

export default defineComponent({
  components: {
    Vue3RulerTool
  },
  setup() {
    let presetLine = ref([{ type: 'h', site: 200 }, { type: 'v', site: 100 }]);
    let visible = ref(true);
    const input=(list:any)=>{
      presetLine.value=list;
    };
    return { presetLine, visible,input }
  },
})
</script>
<style lang="scss">
#appindex {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
