<template>
  <div class="logger-view">
    <div class="pane-toolbar">
      <VueIcon
        icon="dvr"
      />
      <div class="title">
        {{ 'Logs' }}
      </div>
      <VueButton
        class="icon-button flat"
        icon-left="delete_forever"
        v-tooltip="'Clear logs'"
        @click="clearLogs()"
      />
      <VueIcon
        icon="lens"
        class="separator"
      />
      <VueButton
        class="icon-button flat"
        icon-left="subdirectory_arrow_left"
        v-tooltip="'Scroll to bottom'"
        @click="scrollToBottom()"
      />
      <VueButton
        class="icon-button flat"
        icon-left="close"
        v-tooltip="'Close'"
        @click="close()"
      />
    </div>

      <template slot-scope="{ result: { data } }">
        <template v-if="data && data.consoleLogs">
          <LoggerMessage
            v-for="log of data.consoleLogs"
            :key="log.id"
            :message="log"
            pre
          />

          <div
            v-if="!data.consoleLogs.length"
            class="vue-ui-empty"
          >
            <VueIcon icon="wifi" class="large"/>
            <div>{{ $t('org.vue.components.logger-view.empty') }}</div>
          </div>
        </template>
      </template>

  </div>
</template>

<script>

export default {
  methods: {
    onConsoleLogAdded (previousResult, { subscriptionData }) {
      this.scrollToBottom()
      return {
        consoleLogs: [
          ...previousResult.consoleLogs,
          subscriptionData.data.consoleLogAdded
        ]
      }
    },
    async scrollToBottom () {
      await this.$nextTick()
      const list = this.$refs.logs.$el
      list.scrollTop = list.scrollHeight
    },
    async clearLogs () {
      this.close()
    },
    close () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~@/style/imports"
.logger-view
  background $vue-ui-color-light
  height 124px
  display grid
  grid-template-columns 1fr
  grid-template-rows auto 1fr
  grid-template-areas "toolbar" "logs"
  .vue-ui-dark-mode &
    background $vue-ui-color-darker
  .pane-toolbar
    grid-area toolbar
  .logs
    grid-area logs
    padding 0 $padding-item
    overflow-x hidden
    overflow-y auto
  .logger-message
    font-size 12px
    &:hover
      background rgba($vue-ui-color-primary, .05)
</style>