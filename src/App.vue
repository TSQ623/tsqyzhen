<!-- App.vue -->
<template>
  <div id="app">
    <el-button type="primary" @click="handleClick">点击我</el-button>

    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="日期" width="180"></el-table-column>
      <el-table-column prop="name" label="姓名" width="180"></el-table-column>
      <el-table-column prop="address" label="地址"></el-table-column>
    </el-table>

    <EChartsComponent />
  </div>
</template>

<script>
import EChartsComponent from './components/EChartsComponent.vue';

export default {
  name: 'App',
  components: {
    EChartsComponent,
  },
  data() {
    return {
      tableData: [
        { date: '2023-10-01', name: '张三', address: '北京市朝阳区' },
        { date: '2023-10-02', name: '李四', address: '上海市浦东新区' },
        { date: '2023-10-03', name: '王五', address: '广州市天河区' },
      ],
    };
  },
  methods: {
    handleClick() {
      this.$message('按钮被点击了！');
    },
  },
};
</script>

<style>
#app {
  padding: 20px;
}
</style>