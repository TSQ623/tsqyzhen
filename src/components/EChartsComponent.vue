<!-- EChartsComponent.vue -->
<template>
    <div ref="chart" class="echarts-container"></div>
  </template>
  
  <script>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  import * as echarts from 'echarts';
  
  export default {
    name: 'EChartsComponent',
    setup() {
      const chart = ref(null);
      let chartInstance = null;
  
      const initChart = () => {
        chartInstance = echarts.init(chart.value);
        const option = {
          title: {
            text: '示例图表',
          },
          tooltip: {},
          xAxis: {
            data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
          },
          yAxis: {},
          series: [
            {
              name: '销量',
              type: 'bar',
              data: [5, 20, 36, 10, 10, 20, 5],
            },
          ],
        };
        chartInstance.setOption(option);
      };
  
      onMounted(() => {
        initChart();
        window.addEventListener('resize', () => {
          chartInstance.resize();
        });
      });
  
      onBeforeUnmount(() => {
        if (chartInstance) {
          chartInstance.dispose();
        }
      });
  
      return {
        chart,
      };
    },
  };
  </script>
  
  <style>
  .echarts-container {
    width: 100%;
    height: 400px;
  }
  </style>