<template>
  <div id="browser"></div>
</template>
<script>
import * as echarts from "echarts";
import Vue from "vue";

export default {
  data: function () {
    return {
      option: {
        color:[
            '#22485b',
            '#b0d381',
            '#db9e1bc3',
            '#6fa55f',
            '#7cb4cc'
          ],
        backgroundColor: "rgba(229, 228, 216, 0.795)",
        title:{
          text: "浏览器占比",
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
        tooltip: {
          trigger: "item",
        },

        series: [
          {
            name: "Access From",
            type: "pie",
            radius: "50%",
            data: [
             
            ],
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: "rgba(0, 0, 0, 0.5)",
              },
            },
          },
        ],
      },
      };
    },
  mounted: function () {
    // 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById("browser"));
    Vue.axios.get("http://120.79.249.192:8081/web/browser").then((response) => {
      this.option.series[0].data = response.data;
      // 绘制图表
      this.option = { ...this.option };
      myChart.setOption(this.option);
    });
  },
};
</script>
<style scoped>
#browser {
  width: 100%;
  height: 100%;
}
</style>