<script>
export default {
  render: function(createElement) {
    return createElement("div", {
      attrs: {
        id: "main"
      },
      style: {
        height: "600px"
      }
    });
  },
  data(){
      return {
          dataList:[
            {name:"南海诸岛",value:0},
            {name: '北京', value: 1000},
            {name: '天津', value: 200},
            {name: '上海', value: 231},
            {name: '重庆', value: 345},
            {name: '河北', value: 23},
            {name: '河南', value: 5},
            {name: '云南', value: 12},
            {name: '辽宁', value: 567},
            {name: '黑龙江', value: 34},
            {name: '湖南', value: 621},
            {name: '安徽', value: 2},
            {name: '山东', value: 212},
            {name: '新疆', value: 108},
            {name: '江苏', value: 121},
            {name: '浙江', value: 235},
            {name: '江西', value: 721},
            {name: '湖北', value: 231},
            {name: '广西', value: 231},
            {name: '甘肃', value: 876},
            {name: '山西', value: 91},
            {name: '内蒙古', value: 231},
            {name: '陕西', value: 9},
            {name: '吉林', value: 877},
            {name: '福建', value: 231},
            {name: '贵州', value: 231},
            {name: '广东', value: 231},
            {name: '青海', value: 231},
            {name: '西藏', value: 231},
            {name: '四川', value: 231},
            {name: '宁夏', value: 0},
            {name: '海南', value: 0},
            {name: '台湾', value: 0},
            {name: '香港', value: 0},
            {name: '澳门', value: 0}
        ]
      }
  },
  methods: {
    initEchart() {
        var myChart = echarts.init(document.getElementById('main'));
        var option = {
            tooltip: {
                //数据格式化
                formatter:function(params, callback){
                    return params.seriesName+'<br />'+params.name+'：'+params.value
                }
            },
            visualMap: {
                min: 0,
                max: 1000,
                left: 'left',
                top: 'bottom',
                text: ['高','低'],//取值范围的文字
                inRange: {
                    color: ['#e0ffff', 'red']//取值范围的颜色
                },
                show:true//图注
            },
            geo: {
                map: 'china',
                roam: false,//不开启缩放和平移
                zoom:1.23,//视角缩放比例
                label: {
                    normal: {
                        show: true,
                        fontSize:'10',
                        color: 'rgba(0,0,0,0.7)'
                    }
                },
                itemStyle: {
                    normal:{
                        borderColor: 'rgba(0, 0, 0, 0.2)'
                    },
                    emphasis:{
                        areaColor: 'yellow',//鼠标选择区域颜色
                        shadowOffsetX: 0,
                        shadowOffsetY: 0,
                        shadowBlur: 20,
                        borderWidth: 0,
                        shadowColor: 'rgba(0, 0, 0, 0.5)'
                    }
                }
            },
            // 鼠标悬浮提示框
            series : [
                {
                    name: '省份',
                    type: 'map',
                    geoIndex: 0,
                    data:this.dataList
                }
            ]
        };
        myChart.setOption(option);
        myChart.on('click', function (params) {
            alert(params.name);
        });
    }
  },
  mounted() {
    this.initEchart();
  }
};
</script>