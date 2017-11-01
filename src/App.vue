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
  background: green;
}

main {
  display: flex;
  flex: 1;
  > .editor {
    width: 20em;
  }
  > .preview {
    flex: 1;
  }
}
</style>