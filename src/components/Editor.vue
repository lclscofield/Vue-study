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
        <ArrayEditor :items="message" :title="'个人信息'" :labels="{name: '名字', birth: '出身年月', city: '城市'}" :seen="false"></ArrayEditor>
      </li>
      <li :class="{active: currentTab === 1}">
        <ArrayEditor :items="workHistory" :title="'工作经历'" :labels="{company:'公司', content:'工作内容'}" :seen="true"></ArrayEditor>
      </li>
      <li :class="{active: currentTab === 2}">
        <ArrayEditor :items="studyHistory" :title="'学习经历'" :labels="{school:'学校', duration:'学习时间', degree:'学位'}" :seen="true"></ArrayEditor>
      </li>
      <li :class="{active: currentTab === 3}">
        <ArrayEditor :items="projects" :title="'项目经历'" :labels="{name:'项目名称', content:'项目内容'}" :seen="true"></ArrayEditor>
      </li>
      <li :class="{active: currentTab === 4}">
        <ArrayEditor :items="awards" :title="'获奖情况'" :labels="{name:'获奖详情'}" :seen="true"></ArrayEditor>
      </li>
      <li :class="{active: currentTab === 5}">
        <ArrayEditor :items="call" :title="'联系方式'" :labels="{phone:'电话', qq:'QQ', email:'邮件'}" :seen="false"></ArrayEditor>
      </li>
    </ol>
  </div>
</template>

<script>
import ArrayEditor from './ArrayEditor'
export default {
  components: { ArrayEditor },
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
      message: [[{ name: '', birth: '', city: '' }]],
      workHistory: [[{ company: '' }, { content: '' }]],
      studyHistory: [[{ school: '', duration: '', degree: '' }]],
      projects: [[{ name: '' }, { content: '' }]],
      awards: [[{}, { name: '' }]],
      call: [[{ phone: '', qq: '', email: '' }]]
    }
  },
  methods: {}
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
  }
}
</style>