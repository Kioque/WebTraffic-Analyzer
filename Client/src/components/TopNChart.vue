<template>
  <div id="topN"></div>
</template>
<script>
import * as echarts from "echarts";
import Vue from "vue";

export default {
  data: function () {
    return {
      option: {
        borderRadius: 5,
        color:[
            '#22485b',
            '#b0d381',
            '#8fd3e8',
            '#d6be72',
            '#6fa55f',
            '#7cb4cc'
          ],
        backgroundColor: "rgba(229, 228, 216, 0.795)",
        title: {
          text: "访问Url",
          left: "center",
          top: "5%",
          textStyle: {
            fontSize: "14",
            color: "#171819",
          },
        },
        toolbox: {
          show: true,
          feature: {
            mark: { show: true },
            dataView: { show: true, readOnly: false },
            restore: { show: true },
            saveAsImage: { show: true },
          },
        },
        series: [
          {
            name: "Nightingale Chart",
            type: "pie",
            radius: [25, 90],
            center: ["50%", "50%"],
            roseType: "area",
            itemStyle: {
              borderRadius: 8,
            },
            data: [
              { value: 40, name: "rose 1" },
              { value: 38, name: "rose 2" },
              { value: 32, name: "rose 3" },
              { value: 30, name: "rose 4" },
              { value: 28, name: "rose 5" },
              { value: 26, name: "rose 6" },
              { value: 22, name: "rose 7" },
              { value: 18, name: "rose 8" },
            ],
          },
        ],
      },
    };
  },
  mounted: function () {
    // 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById("topN"));
    Vue.axios.get("http://120.79.249.192:8081/web/topN").then((response) => {
      this.option.series[0].data = response.data;
      // 绘制图表
      this.option = { ...this.option };
      myChart.setOption(this.option);
    });
  },
};
</script>
<style scoped>
#topN {
  width: 100%;
  height: 100%;
}
</style>