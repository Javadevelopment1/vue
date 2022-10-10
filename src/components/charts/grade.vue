<template>
  <div id="grade">
    <div ref="box" class="box"></div>
    <div class="notFound" v-if="inNull">
    <i class="iconfont icon_LC_icon_tips_fill"></i><span>该考生为参加考试</span>
    </div>
  </div>
</template>

<script>
  export default {
    name:"grade",
    data(){
      return {
        isNull: false,
        tableDataX:[],
        tableDataY:[],
      }
    },
    mounted(){
      this.score();
    },
    methods:{
      score(){
        let studentId = this.$route.getStudentId
        this.$axios('/api/score/${studentId}').then(res => {console.log(res)
        if(res.data.code == 200){
          let rootData = res.data.data
          rootData.forEach((element,index) =>{
            this.tableDataX.push('第${index + 1}')
            this.tableDataY.push('element.etScore')
          });
          let boxDom = this.$refs["box"];
          let scoreCharts = this.$echarts.init(boxDom);
          let option = {
            xAxis:{
              type: "category",
              data:this.tableDataX
            },
            yAxis:{
              type: "value"
            },
            series:[
              {
                data:this.tableDataY,
                type: "line",
                itemStyle: {normal: {label:{show:true}}}
              }
            ]
          };
          scoreCharts.setOption(option);
          scoreCharts.on("mouseover",params =>{
            console.log(params.value);
          });
        }else{
          this.inNull = true
        }
      })
      }
    }
  };
</script>

<style lang="scss" scoped>
#grade{
  position:relative;
  .box {
    width: 600px;
    height: 400px;
  }
  .notFound{
    position: absolute;
    top: 0;
    left: 0;
  }
}
</style>