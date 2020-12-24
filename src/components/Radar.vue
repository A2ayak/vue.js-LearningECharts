<template>
  <div class="radar" ref="radar" style="width: 100%; height: 100%;"></div>
</template>

<script>
  export default {
    name: "Radar",
    data() {
      return {
        myChart: null
      }
    },
    methods: {
      //初始化图表
      initChart(){
        // 基于准备好的dom，初始化echarts实例
        this.myChart = this.$echarts.init(this.$refs.radar)
        let initOptions = {
          tooltip: {}, //hover时显示内容
          //图例
          legend: {
            top: '40',
            orient:'vertical',
            right: '10',
            icon: 'circle',  //图例类型
            itemWidth: 14,  //图例宽
            itemHeight: 14, //图例高
            data: ['小明', '小红'],
            itemGap: 18 , //图例间隔
            textStyle: {
              color: '#333333',
              fontSize: 12
            } //图例文字大小
          },
          series: [{
            name: '成绩对比',  //图的名字
            type: 'radar', //图的类型
            data: [
              {
                name: '小明',
                value: [80,80,80,80,80,80,80,50],
                symbol: 'circle', //数据点类型为圆形
                symbolSize: 8, //数据点大小
                lineStyle: {
                  normal: {
                    color: '#F36065', width: 1
                  },
                  emphasis: {
                    color: '#F36065', width: 3
                  }
                }, //数据边框线样式
                areaStyle: {
                  color: 'rgba(68, 166, 236, .3)'
                }, //小明的内圈颜色
                emphasis: {
                  areaStyle: {
                    color: '#f9f9f9'
                  }, //激活时内圈颜色
                }, //悬浮时
                itemStyle: {
                  normal: {
                    color: '#5aa9e6',
                  },
                },  //数据点颜色
              },
              {
                name: '小红',
                value: [60,70,68,60,60,80,60,60],
                symbol: 'none', //数据点类型
                // symbolSize: 8,  //数据点大小，这个数据点为none不显示
                lineStyle: {
                  normal: {
                    color: '#33A4FA', width: 1
                  },
                  emphasis: {
                    color: '#33A4FA', width: 3
                  }
                }, //数据边框线样式
                areaStyle: {
                  color: {
                    type: 'linear',
                    x: 0, y: 0,
                    x2: 0, y2: 1,  //（0，0）到（0，1）渐变，即从上往下
                    colorStops: [
                      {
                        offset: 0, color: 'rgba(222, 108, 131, .1)' // 0% 处的颜色
                      }, {
                        offset: 1, color: 'rgba(222, 108, 131, 1)' // 100% 处的颜色
                      }],
                  }
                }, //小红的内圈颜色
                itemStyle: {
                  normal: {
                    color: 'rgba(222, 108, 131, 1)',
                  },
                }, //数据点颜色
              },
            ]
          }],
          grid: {
            top: '0',
            left: '0',
            right: '0',
            bottom: '0',
            containLabel: true
          },
          radar: {
            center: ['50%' , '50%'], //中心位置
            radius: 120, //扩散大小，关乎图形大小
            indicator: [
              { name: '语文', max: 100 },
              { name: '数学', max: 100 },
              { name: '英语', max: 100 },
              { name: '物理', max: 100 },
              { name: '化学', max: 100 },
              { name: '政治', max: 100 },
              { name: '历史', max: 100 },
              { name: '生物', max: 100 },
            ], //类目
            splitNumber: 5, //圈数
            splitLine: {
              show: false,
              lineStyle: {
                color: 'rgba(0, 146, 254, .3)'
              }
            }, //外圈颜色
            name: {
              textStyle: {
                color: '#fff',
                fontSize: 14,
                fontFamily: 'PingFangSC-Regular, PingFang SC',
                fontWeight: 400,
                backgroundColor: '#39a0ed',
                borderRadius: 2,
                padding: [5,8]  //上下-左右padding
              }
            }, //外圈文字
            nameGap: 10, //外圈文字间隔
            axisLine: {
              show : false,
              symbol : 'none',
              lineStyle: {
                color: 'rgba(0, 146, 254, .3)',
                width: 1,
              }
            }, // 网格内的中心射线
            splitArea: {
              show: true,
              areaStyle: {
                color: ['#F4F8FF', '#EDF3FF']
              }
            }, // 分隔区域样式设置
          }
        }
        // 绘制图表
        this.myChart.setOption(initOptions);
      },
    },
    mounted() {
      this.initChart()
    }
  }
</script>

<style scoped>

</style>