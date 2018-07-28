<template>
  <div class="nav-content">
    <NavIntro class="nav-intro"></NavIntro>
    <LogicBuilder class="content vue-ui-disable-scroll"></LogicBuilder>
  </div>
</template>

<script>
export default {
  name: 'MainContent'
}
</script>

<style lang="stylus" scoped>
@import "~@/style/imports"

.nav-content
  width 100%
  height 100%
  display grid
  grid-template-columns 300px 1fr
  grid-template-rows 1fr
  grid-template-areas "nav content"
  > .nav-intro
    grid-area nav
  > .content
    grid-area content
    overflow-x hidden
    overflow-y auto
</style>
