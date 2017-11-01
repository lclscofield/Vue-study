<template>
	<div id="app">
		<Topbar></Topbar>
    <Editor></Editor>
    <Preview></Preview>
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

<style>

</style>