<template>
  <div class="right-statics-bar" ref="rightStaticsBar" style="width: 100%; height: 100%;"></div>
</template>

<script>
  export default {
    name: "Bar",
    data() {
      return {
        myChart: null
      }
    },
    methods: {
      initChart() {
        // 基于准备好的dom，初始化echarts实例
        this.myChart = this.$echarts.init(this.$refs.rightStaticsBar);
        this.myChart.setOption(
            {
              //全局柱状条颜色（局部没有设置则使用该颜色）
              textStyle: {color: '#c6ac8f'},
              //hover相关配置，可用formatter自定义，可参考其他组件formatter
              tooltip: {
                trigger: 'axis'
              },
              //图表在容器中的上下左右距离调整，类似padding
              grid: {
                top: '40',
                left: '10',
                right: '90',
                bottom: '40',
                containLabel: true  // 坐标紧贴边缘
              },
              //X轴相关配置
              xAxis: {
                show: true,
                splitLine : {show : false}, //去掉背景板的网格线
                axisLabel : {show : true}, //坐标轴刻度标签的相关设置
                axisLine : {lineStyle : {color : '#000'},show: true}, //X轴线设置
                axisTick : {lineStyle : {color : '#000'},show: true}, //X轴刻度设置
              },
              //Y轴相关配置
              yAxis: {
                data: [ '业务一', '业务二',  '业务三', '业务四', '业务五' ],
                axisLabel : {
                  show : true,
                  textStyle : {
                    color : '#d76a03',
                    fontSize: 12    /*文字大小*/
                  }
                }, //Y轴文字
                axisLine : {
                  lineStyle : {
                    color : '#ec9f05', //轴的颜色
                    opacity: '1'
                  }
                }, //Y轴线设置
                axisTick:{ show:false }, //Y轴刻度设置
              },
              //图表数据以及样式相关
              series: [
                {
                  showBackground: true, //显示背景框(图中褐色背景柱状条)
                  // backgroundStyle: {color: '#183263'}, //可以单独设置褐色背景柱状条
                  type: 'bar', //类型
                  label : {
                    //通常状态，即不选中状态
                    normal : {
                      show : true,//显示数字
                      position : ['35%','15%'],
                      color: '#ffffff',
                      fontSize: 12,
                      formatter: function (item) {
                        return item.value > 10000 ?  (item.value / 10000).toFixed(2) + 'w' : item.value
                      }
                    }
                  },
                  barWidth : 18,//柱状条宽度
                  itemStyle : {
                      normal : {
                          color:'#495867',//柱状条颜色
                          label : {
                              textStyle : {
                                  fontSize : '15', //柱状条上的显示的文字大小
                                  color:'#fff'
                              }
                          }
                      }
                  },
                  data: [5000, 60000, 8000, 30000, 9000], //假数据
                }
              ]
            }
        )
      },
    },
    mounted() {
      this.initChart()
    }
  }
</script>

<style scoped>

</style>