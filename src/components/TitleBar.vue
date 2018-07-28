<template>
  <div class="title-bar">
    <p class="title">Logic Circuit Simulator</p>
  </div>
</template>

<script>
export default {
  name: 'TitleBar',
  props: {
    title: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
@import "~@/style/imports"

.title-bar
  margin-left auto
  margin-right auto
  background $vue-ui-color-light
  padding 6px
  h-box()
  align-items center
  position relative
  height 36px
  z-index 1
  box-shadow 0 2px 10px rgba(black, .05)
  .vue-ui-dark-mode &
    background $vue-ui-color-darker
    box-shadow 0 2px 10px rgba(black, .2)

.title
  text-align center
  color: blue
  font-size 26px
  font-weight bold

</style>
