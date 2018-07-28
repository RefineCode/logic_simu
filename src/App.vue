<template>
  <div id="app" class="app">
    <TitleBar/>
    <TopBar/>
    <MainContent class="content"></MainContent>
    <StatusBar/>
  </div>
</template>

<script>

export default {
  name: 'app'
}


</script>
<style lang="stylus">
@import "~@vue/ui/dist/vue-ui.css"
@import "~@/style/main"
</style>

<style lang="stylus" scoped>
@import "~@/style/imports"

.app
  display flex
  flex-direction column

.status-bar
  flex auto 0 0


.content
  flex auto 1 1
  height 100%
  overflow hidden

.app-init-loading
  z-index 100000
</style>
