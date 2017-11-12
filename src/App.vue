<template>
  <div id="app">
    <Topbar class="topbar"></Topbar>
    <main>
      <Editor class="editor"></Editor>
      <Preview class="preview"></Preview>
    </main>
  </div>
</template>

<script>
import Topbar from "./components/Topbar";
import Editor from "./components/EDITOR";
import Preview from "./components/Preview";
export default {
  components: {
    Topbar,
    Editor,
    Preview
  }
};
</script>

<style lang="scss">
#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.topbar {
  position: relative;
  z-index: 1;
  box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
}

.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

main {
  display: flex;
  flex: 1;
  background: #ddd;
  > .editor {
    width: 40em;
    margin: 16px 8px 16px 16px;
    background: white;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
    border-radius: 4px;
    overflow: hidden;
  }
  > .preview {
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: white;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
    border-radius: 4px;
    overflow: hidden;
  }
}
</style>