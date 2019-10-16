<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="less">
  @fontsize:10px;
.size{
  width: 100%;
  height: 100%;
}
html,body{
  .size;
  font-size: @fontsize;
  overflow: hidden;
  margin: 0;
  padding: 0;
}
#app {
  .size;
}
</style>
