<template>
  <div id="work">
    <h2>工作经历</h2>
    <div class="work">
      <el-form v-for="(work, index) in workHistory" :key="index">
        <el-form-item label="公司">
          <el-input v-model="work.company"></el-input>
        </el-form-item>
        <el-form-item label="工作内容">
          <el-input type="textarea" :rows="5" v-model="work.content"></el-input>
        </el-form-item>
        <i class="el-icon-circle-close-outline" @click="removeWorkHistory(index)"></i>
      </el-form>
      <el-button type="primary" icon="el-icon-circle-plus-outline" round @click="addWorkHistory"></el-button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['workHistory'],
  methods: {
    addWorkHistory() {
      this.workHistory.push([{ company: '', content: '' }])
    },
    removeWorkHistory(index) {
      this.workHistory.splice(index, 1)
    }
  }
}
</script>

<style lang="scss">
#work {
  > .work {
    > .el-form {
      position: relative;
      > .el-icon-circle-close-outline {
        position: absolute;
        top: 12px;
        right: 0;
        cursor: pointer;
      }
    }
    > .el-button {
      margin: 10px;
    }
  }
}
</style>
