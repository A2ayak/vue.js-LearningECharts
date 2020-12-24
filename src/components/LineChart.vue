<template>
  <div style="width: 100%; height: 100%;">
    <div class="chart" ref="myChart" style="width: 100%; height: 100%;"></div>
  </div>
</template>

<script>
  export default {
    name: "LineChart",
    data() {
      return {
        myChart: null,
      }
    },
    methods: {
      initChart() {
        // 基于准备好的dom，初始化echarts实例
        this.myChart = this.$echarts.init(this.$refs.myChart)
        let initOptions = {
          //图在容器内的位置，不需要调整外部margin或padding
          grid: {
            top: '27px',
            left: '50px',
            right: '50px',
            bottom: '50px'
          },
          //X轴相关配置
          xAxis: {
            // gridIndex: 10,
            offset: 10,  //X轴到文字的距离
            type: 'category',  //坐标轴类型，这里category表示类目
            // boundaryGap: false,   //控制坐标轴文字是否对应刻度
            data: ['1月01日', '1月02日', '1月03日', '1月04日'],
            axisTick: { show: true }, //X坐标轴引导线
            axisLine: { show: true }, //X坐标轴线
            axisLabel: {
              fontSize: 14,
              // fontWeight: 'bold',
              color: '#333333',
            }   //X轴文字样式
          },
          //Y轴相关配置
          yAxis: {
            splitLine: {
              lineStyle:{
                type: 'dashed',
                width: 1,
                color: '#E7E7E7'
              }  //坐标轴背面刻度样式
            } ,   //背景分割线
            type: 'value', //坐标轴类型，value表示数值
            axisLine: { show: true}, //Y坐标轴线
            axisTick: { show: true }, //Y坐标轴引导线，坐标轴中凸出来的细线
            axisPointer: {
              show: true,
              lineStyle: {
                type: 'dashed',
                width: 2
              }
            }, //鼠标移入的横向网格线的样式
            axisLabel: {
              fontSize: 14,
              // fontWeight: 'bold',
              color: '#333333',
            } //Y轴文字样式
          },
          //图表内容相关配置
          series: [{
            data: [820, 932, 901, 934, 1290, 1330, 1320], //数据放在这里
            type: 'line',   //类型：折线图
            showSymbol: true, //显示图中的白色空心原点
            symbolSize: ['10', '10'],  //图中的白色空心原点的大小
            itemStyle: {
              normal: {
                borderColor:'#297adc'
              },  //通常样式
              emphasis: {
                color: '#ffffff',
                borderColor:'#297adc'
              }  //hover样式
            },
            areaStyle: {
              color: {
                type: 'linear',   //线性
                x: 0, y: 0,
                x2: 1, y2: 0,  //从（0，0）到（1，0），即左到右的方向渐变
                colorStops: [
                    {
                  offset: 0, color: '#fff' // 0% 处的颜色
                }, {
                  offset: 0.2, color: '#35A7FF' // 20% 处的颜色
                },{
                  offset: 1, color: '#35A7FF' // 100% 处的颜色
                }
                ],
                global: false // 缺省为 false
              }  //渐变色设置
            },  //折线下包围的区域样式
            lineStyle: {
              // color: '#ffffff',
              color: '#35A7FF',
              width: 2
            }, //折线样式
            // smooth: true,   //是否平滑
          }],
          //鼠标hover悬浮到点上时显出的数据框
          tooltip : {
            trigger: 'axis',
            axisPointer: {
              type: 'line',
              label: {
                backgroundColor: '#ffffff',
                fontWeight: 600,
                color: '#4D66FF',
                border: 'none'
              },
              lineStyle: {
                type: 'dashed',
                width: 2
              } //数据竖线样式
            },
            backgroundColor: '#ffffff',
            textStyle: {
              color: '#36425A'
            },
            padding: 0,
            formatter: item => {
              let titleArr = ['发放积分']
              return `<div class="special-tooltip"><span class="title">标题自定义</span>` + `<br/>` +
                  `<div class="inner-item"><span style="width: 5px;height: 5px;
                      background-color: #00aaee;border-radius: 50%;display: inline-block"></span><div class="content">
                      ${titleArr[0]}：${item[0].data}</div></div>` + `</div>`
            },  //自定义，箭头函数为了取到data数值
          },
        }
        // 绘制图表
        this.myChart.setOption(initOptions);
      },
      //获取数据查询始末日期
    },
    mounted() {
      this.initChart()
    }
  }
</script>

<style scoped lang="less">
  /*图表悬浮框定制样式*/
  /deep/.special-tooltip {
    width: 155px;
    height: 57px;
    background: rgba(255, 255, 255, 0.8);
    box-shadow: 0px 2px 34px 0px rgba(0, 0, 0, 0.08);
    border-radius: 6px;
    padding: 13px 0 0 17px;
    .title {
      float: left;
      font-size: 16px;
      font-weight: 600;
    }
    .inner-item {
      /*border: 1px solid red;*/
      display: flex;
      align-items: center;
      padding-top: 10px;
      .content {
        display: inline-block;
        margin-left: 9px;
      }
    }
  }
</style>