<template>
<section class="add">
  <el-form ref="form" :model="form" label-width="80px">
  <el-form-item label="姓名">
    <el-input v-model="form.teacherName"></el-input>
  </el-form-item>
  </el-form>
</section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>

</style>
