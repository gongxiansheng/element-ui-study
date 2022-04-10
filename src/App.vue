<template>
  <div id="app">
    <el-card class="box-card">
      <el-tabs v-model="activeName" @tab-click="handleClick">
        <el-tab-pane v-for="item in tabs" :key="item.value" :label="item.label" :name="item.value"></el-tab-pane>
      </el-tabs>
      <component :is="activeComponent" />
    </el-card>
  </div>
</template>

<script>
import eCascader from './components/Cascader.vue'
export default {
  name: 'App',
  components: {
    eCascader
  },
  data() {
    return {
      activeName: 'first',
      tabs: [
        {
          value: 'first',
          label: '用户管理',
          component: 'eCascader'
        }
      ]
    }
  },
  computed: {
    activeComponent() {
      const tab = this.tabs.find(item => item.value === this.activeName)
      return tab.component
    }
  },
  methods: {
    handleClick() {}
  }
}
</script>

<style>
html,
body {
  margin: 0;
  height: 100%;
}
#app {
  height: 100%;
  padding: 20px;
  box-sizing: border-box;
}
.box-card {
  height: 100%;
}
</style>
