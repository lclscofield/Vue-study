<template>
  <div id="preview">
    <section>
      <h2>{{ shareData.message[0][0].name || '请填写名字' }}</h2>
      <p> {{ shareData.message[0][0].birth || '请填写出身年月' }} | {{ shareData.message[0][0].city || '请填写城市' }}</p>
    </section>

    <section v-if="filter(shareData.studyHistory).length > 0">
      <h2>学习经历</h2>
      <div v-for="(item, index) in filter(shareData.studyHistory)" :key="index">
        <p>{{ filter(shareData.studyHistory)[index][0].school || '请填写学校' }} | {{ filter(shareData.studyHistory)[index][0].duration || '请填写学习时间' }} | {{ filter(shareData.studyHistory)[index][0].degree || '请填写学位' }}</p>
      </div>
    </section>

    <section v-if="filter(shareData.workHistory).length > 0">
      <h2>工作经历</h2>
      <div v-for="(item, index) in filter(shareData.workHistory)" :key="index">
        <h3>{{ filter(shareData.workHistory)[index][0].company || '请填写公司名称' }}</h3>
        <p>{{ filter(shareData.workHistory)[index][1].content || '请填写工作内容' }}</p>
      </div>
    </section>

    <section v-if="filter(shareData.projects).length > 0">
      <h2>项目经历</h2>
      <div v-for="(item, index) in filter(shareData.projects)" :key="index">
        <h3>{{ filter(shareData.projects)[index][0].name || '请填写项目名称' }}</h3>
        <p>{{ filter(shareData.projects)[index][1].content || '请填写项目内容' }}</p>
      </div>
    </section>

    <section v-if="filter(shareData.awards).length > 0">
      <h2>获奖情况</h2>
      <div v-for="(item, index) in filter(shareData.awards)" :key="index">
        <p>{{ filter(shareData.awards)[index][1].content || '请填写获奖详情' }}</p>
      </div>
    </section>

    <section>
      <h2>联系方式</h2>
      <p>电话：
        <span>{{ shareData.call[0][0].phone || '请填写电话' }}</span>
      </p>
      <p>QQ：
        <span>{{ shareData.call[0][0].qq || '请填写QQ' }}</span>
      </p>
      <p>邮件：
        <span>{{ shareData.call[0][0].email || '请填写邮件' }}</span>
      </p>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      shareData: {
        message: [[{ name: '', birth: '', city: '' }]],
        workHistory: [[{ company: '' }, { content: '' }]],
        studyHistory: [[{ school: '', duration: '', degree: '' }]],
        projects: [[{ name: '' }, { content: '' }]],
        awards: [[{}, { content: '' }]],
        call: [[{ phone: '', qq: '', email: '' }]]
      }
    }
  },
  created() {
    this.$root.bus.$on('shareData', value => {
      this.shareData = value
    })
  },
  methods: {
    filter(arr) {
      return arr.filter(item => {
        // 根据对象的值为不为空决定是否显示本模块
        return !this.isEmpty(item)
      })
    },
    isEmpty(arr) {
      let empty = true
      // 如果第一个对象存在 key
      if (Object.getOwnPropertyNames(arr[0]).length !== 0) {
        for (let key1 in arr[0]) {
          // 如果第一个对象有一个 key 的值不为空就返回不为空
          if (arr[0][key1]) {
            empty = false
            return empty
          }
        }
        // 如果第一个对象 key 值全为空
        if (empty && arr[1]) {
          for (let key2 in arr[1]) {
            // 如果第二个对象有一个 key 的值不为空就返回不为空
            if (arr[1][key2]) {
              empty = false
              return empty
            }
          }
        }
      } else {
        if (arr[1]) {
          for (let key2 in arr[1]) {
            // 如果第二个对象有一个 key 的值不为空就返回不为空
            if (arr[1][key2]) {
              empty = false
              return empty
            }
          }
        }
      }
      return empty
    }
  }
}
</script>


<style lang="scss">
#preview {
  overflow: auto;
  h2 {
    margin: 20px 0 0 20px;
  }
  h3,
  p {
    margin: 10px 0 0 20px;
  }
}
</style>