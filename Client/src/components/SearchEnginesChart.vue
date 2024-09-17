<template>
  <div id="search"></div>
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
            '#d6be72',
            '#6fa55f',
            '#7cb4cc'
          ],
        backgroundColor: "rgba(229, 228, 216, 0.795)",
        title: {
          text: "搜索引擎",
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
        legend: {
          top: "bottom",
          left: "center",
        },
        series: [
          {
            name: "Access From",
            type: "pie",
            radius: ["40%", "70%"],
            avoidLabelOverlap: false,
            itemStyle: {
              borderRadius: 10,
              borderColor: "#fff",
              //更改描边
              borderWidth: 0,
            },
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: "40",
                fontWeight: "bold",
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: 1048, name: "Search Engine" },
              { value: 735, name: "Direct" },
              { value: 580, name: "Email" },
              { value: 484, name: "Union Ads" },
              { value: 300, name: "Video Ads" },
            ],
          },
        ],
      },
    };
  },
  mounted: function () {
    var myChart = echarts.init(document.getElementById("search"));
    Vue.axios.get("http://120.79.249.192:8081/web/search").then((response) => {
      this.option.series[0].data = response.data;
      // 绘制图表
      this.option = { ...this.option };
      myChart.setOption(this.option);
    });
  },
};
</script>
<style scoped>
#search {
  width: 100%;
  height: 100%;
}
</style>