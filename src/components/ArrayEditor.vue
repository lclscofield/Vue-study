<template>
  <div id="work">
    <h2>{{title}}</h2>
    <div class="work">
      <el-form v-for="(item, index) in items" :key="index">
        <el-form-item :label="labels[key]" v-for="(key, index) in keys1" :key="index">
          <el-input v-model="item[0][key]"></el-input>
        </el-form-item>
        <div v-if="item[1]">
          <el-form-item :label="labels[key]" v-for="(key, index) in keys2" :key="index">
            <el-input type="textarea" :rows="5" v-model="item[1][key]"></el-input>
          </el-form-item>
        </div>
        <i v-if="seen" class="el-icon-circle-close-outline" @click="removeItems(index)"></i>
        <hr v-if="seen">
      </el-form>
      <el-button v-if="seen" type="primary" icon="el-icon-circle-plus-outline" round @click="addItems"></el-button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['items', 'labels', 'seen', 'title'],
  computed: {
    keys1() {
      return Object.keys(this.items[0][0])
    },
    keys2() {
      return Object.keys(this.items[0][1])
    }
  },
  methods: {
    addItems() {
      let arr = [{}]
      this.keys1.map(key => {
        arr[0][key] = ''
      })
      if (this.items[0][1]) {
        arr[1] = {}
        this.keys2.map(key => {
          arr[1][key] = ''
        })
      }
      this.items.push(arr)
    },
    removeItems(index) {
      this.items.splice(index, 1)
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
    > .el-form:first-child {
      > .el-icon-circle-close-outline {
        display: none;
      }
    }
    > .el-button {
      margin: 10px;
    }
  }
}
</style>
