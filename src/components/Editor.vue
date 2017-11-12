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
      <li v-for="i in [0,1,2,3,4,5]" :key="i" :class="{active: currentTab === i}">
        tab {{i}}
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
      ]
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
  > .panes > li {
    display: none;
    &.active {
      display: block;
      transition: display 0.5s;
    }
  }
}
</style>