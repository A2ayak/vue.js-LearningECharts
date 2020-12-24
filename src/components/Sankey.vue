<template>
  <div class="sankey" ref="sankey" style="width: 100%; height: 100%;"></div>
</template>

<script>
  export default {
    name: "Sankey",
    data() {
      return {
        myChart: null
      }
    },
    methods: {
      //初始化图表
      initChart() {
        // 基于准备好的dom，初始化echarts实例
        this.myChart = this.$echarts.init(this.$refs.sankey)
        let initOptions = {
          //图表内容数据
          series: {
            type: 'sankey',
            focusNodeAdjacency: 'allEdges', //鼠标 hover 到节点或边上，相邻接的节点和边高亮的交互
            label: {
              fontSize: 16,
              fontFamily: 'Helvetica',
              color: '#4F5D79',
              lineHeight: 22,
              distance: 19
            },
            nodeWidth: 12,
            width: 400,
            height: 300, //图表大小
            left: 'center', //居中
            top: 'middle', //居中
            data: [
              {
                name: '首页',  //类名
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#4d09ff' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#770afd' // 100% 处的颜色
                    }],
                  },
                },  //颜色设置
              }, {
                name: '商品分类',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#f8067c' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#ff0d9d' // 100% 处的颜色
                    }],
                    global: false // 缺省为 false
                  },
                },
                label: {position: 'left'}
              }, {
                name: '商品详情',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#5eb054' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#9ee08d' // 100% 处的颜色
                    }],
                  },
                },
                label: {position: 'left'}
              }, {
                name: '购物车',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#8085fa' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#c0a8ff' // 100% 处的颜色
                    }],
                  },
                },
                label: {position: 'left'}
              }, {
                name: '我的',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#38c5b1' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#69e4d9' // 100% 处的颜色
                    }],
                  },
                },
              }, {
                name: '设置',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#ffbb5b' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#ffdf94' // 100% 处的颜色
                    }],
                  },
                },
                label: {position: 'left'}
              }, {
                name: '清理缓存',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#3abafc' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#77d0ff' // 100% 处的颜色
                    }],
                  },
                },
                label: {position: 'left'}
              }, {
                name: '退出',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#fc7d53' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#ffad92' // 100% 处的颜色
                    }],
                  },
                },
                label: {position: 'left'}
              }, {
                name: '登录',
                itemStyle: {
                  borderWidth: '0',
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 0, y2: 1,
                    colorStops: [{
                      offset: 0, color: '#43e6ea' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#74e7ea' // 100% 处的颜色
                    }],
                  },
                },
                label: {position: 'left'}
              }],  //数据
            links: [
              {
                source: '首页',
                target: '商品分类',
                value: 5, //数值大小
                lineStyle: {
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 1, y2: 0,
                    colorStops: [{
                      offset: 0, color: 'rgba(248,152,124, 1)' // 0% 处的颜色
                    }, {
                      offset: 1, color: 'rgba(248,152,124, .1)' // 100% 处的颜色
                    }],
                  },
                }
              },
              {
                source: '首页',
                target: '商品详情',
                value: 5
              },
              {
                source: '首页',
                target: '购物车',
                value: 5,
                lineStyle: {
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 1, y2: 0,
                    colorStops: [{
                      offset: 0, color: 'rgba(168,192,244, 1)' // 0% 处的颜色
                    }, {
                      offset: 1, color: 'rgba(218,152,184, .7)' // 100% 处的颜色
                    }],
                  },
                }
              },
              {
                source: '首页',
                target: '我的',
                value: 5,
                lineStyle: {
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 1, y2: 0,
                    colorStops: [{
                      offset: 0, color: 'rgba(218,102,184, 1)' // 0% 处的颜色
                    }, {
                      offset: 1, color: 'rgba(218,102,184, .7)' // 100% 处的颜色
                    }],
                  },
                }
              },
              {
                source: '我的',
                target: '设置',
                value: 5
              },
              {
                source: '设置',
                target: '清理缓存',
                value: 5
              },
              {
                source: '我的',
                target: '退出',
                value: 5
              },
              {
                source: '我的',
                target: '登录',
                value: 5,
                lineStyle: {
                  color: {
                    type: 'linear', x: 0, y: 0, x2: 1, y2: 0,
                    colorStops: [{
                      offset: 0, color: 'rgba(118,102,184, 1)' // 0% 处的颜色
                    }, {
                      offset: 1, color: 'rgba(188,102,164, .7)' // 100% 处的颜色
                    }],
                  },
                }
              },
            ]  //路径
          },
          tooltip: {
            trigger: 'item',
            padding: [13, 32, 13, 17],
            backgroundColor: '#fff',
            textStyle: {
              fontSize: 16,
              fontFamily: 'PingFangSC-Semibold, PingFang SC',
              fontWeight: 600,
              color: '#000000',
              lineHeight: 22
            }
          },  //悬浮时的状态
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