<template>
  <div id="ip"></div>
</template>
<script >
import * as echarts from "echarts";
import Vue from "vue";

export default {
  data: function () {
    return {
      option: {
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
          text: "运营商",
          left: "center",
          top: "5%",
          textStyle: {
            fontSize: "14",
            color: "#171819",
          },
        },
        tooltip: {},
        toolbox: {
          show: true,
          feature: {
            mark: { show: true },
            dataView: { show: true, readOnly: false },
            restore: { show: true },
            saveAsImage: { show: true },
          },
          
        },
        yAxis: {
          axisLabel: {
            textStyle: {
              fontSize: "14",
            },
          },
          data: [],
          color:[
            '#9b8bba',
            '#e098c7',
            '#8fd3e8',
            '#71669e',
            '#cc70af',
            '#7cb4cc'
          ],
        },
        xAxis: {},
        series: [
          {
            name: "访问次数",
            type: "bar",
            data: [],
          },
        ],
      },
    };
  },
  mounted: function () {
    // 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById("ip"));

    Vue.axios.get("http://120.79.249.192:8081/web/company").then((response) => {
      var names = response.data.map((item) => item.name);
      var values = response.data.map((item) => item.value);
      this.option.yAxis.data = names;
      this.option.series[0].data = values;
      // 绘制图表
      this.option = { ...this.option };
      myChart.setOption(this.option);

    });

  },
};
</script>
<style scoped>
#ip {
  width: 100%;
  height: 100%;
}
</style>