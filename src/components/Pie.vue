<template>
  <div class="hall-point-contain" style="width: 100%; height: 100%;">
    <div class="ring" ref="ring" style="width: 100%; height: 100%;"></div>
  </div>
</template>

<script>
  export default {
    name: "Pie",
    data() {
      return {
        myChart: null,
      }
    },
    methods: {
      //初始化图表
      initChart(){
        // 基于准备好的dom，初始化echarts实例
        this.myChart = this.$echarts.init(this.$refs.ring)
        let initOptions = {
          //鼠标hover悬浮到点上时显出的数据框
          tooltip: {
            trigger: 'item',
            formatter: '{b}:{c} ({d}%)'
          },
          //标题相关样式
          title:{
            text:"XXXXXXXX我是标题",
            left:"17%", //距离左上角位置
            top:"3%", //距离左上角位置
            textStyle:{
              color:"#33A4FA",
              fontFamily: "Source Han Sans CN",
              fontSize:16,
              align:"center"
            }
          },
          //图例
          legend: [
            {
              // x : 220,
              y : 300, //图例（x，y）坐标位置
              // itemWidth: 12,
              // itemHeight: 8,
              // itemGap: 15,
              orient: 'horizontal', //图例排列方式'horizontal','vertical'
              data: ['业务一', '业务二', '业务三'],
              textStyle: {
                fontSize: 16,
                color: '#33A4FA',
                rich: {
                  0: {
                    fontSize: 20,
                    // fontFamily: '',
                    fontWeight: 'bold',
                    color: '#B7DDDD'
                  }
                }
              },
              //添加legend后的百分比数值,index对应rich
              formatter: function (name) {
                let index = 0;
                let than = initOptions.series[0].data; //获取series中的data
                let total = 0;
                let tarValue;
                for (let i = 0, l = than.length; i < l; i++) {
                  total += than[i].value;
                  if (than[i].name === name) {
                    tarValue = than[i].value;
                  }
                }
                let p = (tarValue / total) * 100;
                return name + " " + " " +"{" + index + "|" + p.toFixed(0) + "%}" ;
              }
            }, //积分汇总legend
            {
              x : 330,
              y : 44,
              orient: 'vertical',
              data: ['业务一子类一', '业务一子类二'],
              itemWidth: 8,
              itemHeight: 8,
              icon: 'circle',
              itemGap: 8,
              textStyle: {
                fontSize: 12,
                color: '#87677B'
              },
              formatter: function (name) {
                let index = 0;
                let than = initOptions.series[1].data; //获取series中的data
                let total = 0;
                let tarValue;
                for (let i = 0, l = than.length; i < l; i++) {
                  if (than[i].name === name) {
                    tarValue = than[i].value;
                    index = Math.floor(i/2)
                    total = initOptions.series[0].data[index].value;
                  }
                }
                let p = (tarValue / total) * 100;
                return name  + " " + p.toFixed(0) + " " + "%";
              }
            }, //业务一子类一回收legend
            {
              x : 330,
              y : 134,
              orient: 'vertical',
              data: ['业务二子类一', '业务二子类二'],
              itemWidth: 8,
              itemHeight: 8,
              icon: 'circle',
              itemGap: 8,
              textStyle: {
                fontSize: 12,
                color: '#87677B'
              },
              formatter: function (name) {
                let index = 0;
                let than = initOptions.series[1].data; //获取series中的data
                let total = 0;
                let tarValue;
                for (let i = 0, l = than.length; i < l; i++) {
                  if (than[i].name === name) {
                    tarValue = than[i].value;
                    index = Math.floor(i/2)
                    total = initOptions.series[0].data[index].value;
                  }
                }
                let p = (tarValue / total) * 100;
                return name  + " " + p.toFixed(0) + " " + "%";
              }
            }, //业务二子类一回收legend
            {
              x : 330,
              y : 224,
              orient: 'vertical',
              data: ['业务三子类一', '业务三子类二'],
              itemWidth: 8,
              itemHeight: 8,
              icon: 'circle',
              itemGap: 8,
              textStyle: {
                fontSize: 12,
                color: '#87677B'
              },
              formatter: function (name) {
                let index = 0;
                let than = initOptions.series[1].data; //获取series中的data
                let total = 0;
                let tarValue;
                for (let i = 0, l = than.length; i < l; i++) {
                  if (than[i].name === name) {
                    tarValue = than[i].value;
                    index = Math.floor(i/2)
                    total = initOptions.series[0].data[index].value;
                  }
                }
                let p = (tarValue / total) * 100;
                return name  + " " + p.toFixed(0) + " " + "%";
              }
            }, //业务三子类一回收legend
          ],
          //图的相关设置
          series: [
            {
              name: '汇总1',
              type: 'pie',
              selectedMode: 'single', //表示是否支持多个图选中，默认关闭
              radius: ['0%', '25%'], //内圈到外圈占比
              label: {
                fontSize: 14,
                fontWeight: 'bold',
                formatter: function (data) {
                  return data.percent.toFixed(0) + '%'
                },
              },
              labelLine:{
                show: true,
                length: 5, //引导线
                length2: 5 //引导线2
              },
              center: ['35%','43%'], //内圈圆心位置
              data: [
                {value: 100, name: '业务一', itemStyle: {color: '#EC4E20'}},
                {value: 200, name: '业务二', itemStyle: {color: '#ff9505'}},
                {value: 300, name: '业务三', itemStyle: {color: '#016fb9'}}
              ]
            },
            {
              name: '汇总2',
              type: 'pie',
              radius: ['48%','58%',],
              label: {
                position: 'outside',
                fontSize: 14,
                fontWeight: 'bold',
                formatter: function (data) {
                  // console.log(data)
                  let index = 0;
                  let than = initOptions.series[1].data; //获取series中的data
                  let total = 0;
                  let tarValue;
                  for (let i = 0, l = than.length; i < l; i++) {
                    if (than[i].name === data.name) {
                      tarValue = than[i].value;
                      index = Math.floor(i/2)
                      total = initOptions.series[0].data[index].value;
                    }
                  }
                  let p = (tarValue / total) * 100;
                  return  p.toFixed(0) + "%"
                }
              },
              labelLine:{
                show: false,
                length: 6,
                length2: 0
              },
              center: ['35%','43%'],
              data: [
                {value: 50, name: '业务一子类一', itemStyle: {color: 'rgba(236, 78, 32, 1)'}},
                {value: 50, name: '业务一子类二', itemStyle: {color: 'rgba(236, 78, 32, .6)'}},
                {value: 120, name: '业务二子类一', itemStyle: {color: 'rgba(255, 149, 5, 1)'}},
                {value: 80, name: '业务二子类二', itemStyle: {color: 'rgba(255, 149, 5, .6)'}},
                {value: 120, name: '业务三子类一', itemStyle: {color: 'rgba(1, 111, 185, 1)'}},
                {value: 180, name: '业务三子类二', itemStyle: {color: 'rgba(1, 111, 185, .6)'}},
              ]
            }
          ]
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

<style scoped lang="less">

</style>