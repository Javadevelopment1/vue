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
  }
</script>

<style lang="scss" scoped>

</style>