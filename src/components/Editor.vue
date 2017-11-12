<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" :key="i" :class="{active: currentTab === i}" @click="currentTab = i">
          <svg class="icon">
            <use :xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panes">
      <li :class="{active: currentTab === 0}">
        <h2>个人信息</h2>
        <el-form>
          <el-form-item label="姓名">
            <el-input v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="出身年月">
            <el-input v-model="profile.birth"></el-input>
          </el-form-item>
          <el-form-item label="城市">
            <el-input v-model="profile.city"></el-input>
          </el-form-item>
        </el-form>
      </li>
      <li :class="{active: currentTab === 1}">
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
      </li>
      <li :class="{active: currentTab === 2}">
        <h2>学习经历</h2>
      </li>
      <li :class="{active: currentTab === 3}">
        <h2>项目经历</h2>
      </li>
      <li :class="{active: currentTab === 4}">
        <h2>获奖情况</h2>
      </li>
      <li :class="{active: currentTab === 5}">
        <h2>联系方式</h2>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentTab: 0,
      icons: [
        'shenfengzheng4',
        'work',
        'book',
        'browse',
        'jiangbei01',
        '3-copy'
      ],
      profile: {
        name: '',
        birth: '',
        city: ''
      },
      workHistory: [{ company: '', content: '' }]
    }
  },
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
#editor {
  display: flex;
  min-height: 100px;
  > nav {
    background: #409eff;
    width: 80px;
    > ol > li {
      padding: 16px 0;
      margin: 8px;
      text-align: center;
      border-radius: 50%;
      cursor: pointer;
      > .icon {
        width: 24px;
        height: 24px;
        fill: white;
      }
      &.active {
        background: white;
        transition: background 0.5s;
        > .icon {
          fill: #409eff;
        }
      }
    }
  }
  > .panes {
    flex: 1;
    > li {
      display: none;
      padding: 32px;
      height: 100%;
      width: 100%;
      overflow: auto;
      &.active {
        display: block;
        transition: display 0.5s;
      }
    }
    .work {
      .el-form {
        position: relative;
        .el-icon-circle-close-outline {
          position: absolute;
          top: 12px;
          right: 0;
          cursor: pointer;
        }
      }
      .el-button {
        margin: 10px;
      }
    }
  }
}
</style>