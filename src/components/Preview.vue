<template>
  <div id="preview">
    {{hahaha.message}}
  </div>
</template>

<script>
export default {
  data() {
    return {
      hahaha: {}
    }
  },
  created() {
    this.$root.bus.$on('shareData', value => {
      this.hahaha = value
    })
  }
}
</script>


<style>
#preview {
}
</style>