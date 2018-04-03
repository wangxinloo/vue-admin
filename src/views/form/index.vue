<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="120px">
      <el-form-item label="用户名">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="负责区域">
        <el-select v-model="form.region" placeholder="选择区域">
          <el-option label="一区" value="shanghai"></el-option>
          <el-option label="二区" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="时间段">
        <el-col :span="11">
          <el-date-picker type="date" placeholder="开始时间" v-model="form.date1" style="width: 100%;"></el-date-picker>
        </el-col>
        <el-col class="line" :span="2">-</el-col>
        <el-col :span="11">
          <el-time-picker type="fixed-time" placeholder="结束时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
        </el-col>
      </el-form-item>
      <el-form-item label="当面付款">
        <el-switch v-model="form.delivery"></el-switch>
      </el-form-item>
      <el-form-item label="类型">
        <el-checkbox-group v-model="form.type">
          <el-checkbox label="线上活动" name="type"></el-checkbox>
          <el-checkbox label="线下活动" name="type"></el-checkbox>
          <el-checkbox label="促销活动" name="type"></el-checkbox>
        </el-checkbox-group>
      </el-form-item>
      <el-form-item label="来源">
        <el-radio-group v-model="form.resource">
          <el-radio label="发起者"></el-radio>
          <el-radio label="现场"></el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="备注">
        <el-input type="textarea" v-model="form.desc"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">提交</el-button>
        <el-button @click="onCancel">反回</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  methods: {
    onSubmit() {
      this.$message('submit!')
    },
    onCancel() {
      this.$message({
        message: 'cancel!',
        type: 'warning'
      })
    }
  }
}
</script>

<style scoped>
.line{
  text-align: center;
}
</style>

