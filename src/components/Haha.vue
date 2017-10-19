<template>
  <div>
    <p>{{nana}}</p>
    <p>{{isHahaha}}</p>
  </div>
</template>

<script>
export default {
  name: "Haha",
  props: ["nana", "text", "isHahaha"]
};
</script>