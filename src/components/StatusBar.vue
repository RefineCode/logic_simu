<template>
  <div class="status-bar">
    <LoggerView
      v-if="showLogs"
      @close="showLogs = false"
    />

    <div class="content">
      <div
        class="section action console-log"
        v-tooltip="'Open'"
        @click="onConsoleClick()"
      >
        <VueIcon icon="dvr"/>
        <LoggerMessage class="last-message"
          v-if="consoleLogLast"
          :message="consoleLogLast"
        />
        <div v-else class="last-message">{{ 'No logs yet' }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  clientState: true,
  data () {
    return {
      showLogs: false,
      consoleLogLast: null
    }
  },
  methods: {
    onConsoleClick () {
      this.$emit('console')
      this.showLogs = !this.showLogs
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~@/style/imports"
.status-bar
  position bottom
  z-index 1
  box-shadow 0 -2px 10px rgba(black, .05)
  .vue-ui-dark-mode &
    box-shadow 0 -2px 10px rgba(black, .2)
  .content
    h-box()
    align-items center
    background #CACACA // $vue-ui-color-light
    font-size 12px
    height 34px
    .vue-ui-dark-mode &
      background $vue-ui-color-darker
  .section
    h-box()
    align-items center
    opacity .8
    padding 0 11px
    height 100%
    cursor default
    &:hover
      opacity 1
      background lighten($vue-ui-color-light-neutral, 30%)
      .vue-ui-dark-mode &
        background $vue-ui-color-dark
    > .vue-ui-icon + *
      margin-left 4px
    .label
      color lighten($vue-ui-color-dark, 20%)
      .vue-ui-dark-mode &
        color lighten($vue-ui-color-dark-neutral, 20%)
    &.action
      user-select none
      cursor pointer
  .console-log
    &,
    .last-message
      flex 100% 1 1
      width 0
    .logger-message
      font-size .9em
      padding-right 0
</style>