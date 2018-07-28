<template>
  <div class="top-bar">
    <div class="pane-toolbar">
      <VueButton
        class="flat custom_width"
        icon-left=""
        v-tooltip="'NAND Gate'"
        @click="selectSymbol('NAND')"
      >
      <svg
         xmlns="http://www.w3.org/2000/svg"
         width="50"
         height="25">
        <path
           d="m 39.5,13 h 8 M 15.5,8 H 2.5 M 16,18 H 2.5"
           style="fill:none;stroke:#000000;stroke-width:1" />
        <path
           d="m 15,3 v 20 h 10.238095 c 5.633954,0 10,-4.500023 10,-10 0,-5.499978 -4.366045,-10 -10,-10 z m 1.428572,1.428571 h 8.809523 c 4.880331,0 8.333334,3.819978 8.333334,8.571429 0,4.751451 -3.691098,8.571428 -8.571429,8.571428 h -8.571428 z"
           style="stroke-width:0.5" />
        <path
           d="m 39.5,13 a 2,2 0 1 1 -4,0 2,2 0 1 1 4,0 z"
           style="fill:none;stroke:#000000;stroke-width:1.5" />
      </svg>
      </VueButton>

      <VueButton
        class="flat custom_width"
        icon-left=""
        v-tooltip="'AND Gate'"
        @click="selectSymbol('AND')"
      >
<svg
   xmlns="http://www.w3.org/2000/svg"
   height="25"
   width="50">
  <defs
     id="defs10" />
  <path
     style="fill:none;stroke:#000000;stroke-width:1"
     id="path2"
     d="m 35,12.5 h 12.5 m -32,-5 H 2.5 M 16,17.5 H 2.5" />
  <path
     style="stroke-width:0.5"
     id="path4"
     d="m 15,2.5 v 20 h 10.238095 c 5.633954,0 10,-4.500023 10,-10 0,-5.4999775 -4.366045,-10 -10,-10 z m 1.428572,1.4285715 h 8.809523 c 4.880331,0 8.333334,3.8199775 8.333334,8.5714285 0,4.751451 -3.691098,8.571428 -8.571429,8.571428 h -8.571428 z" />
</svg>
      </VueButton>

      <VueIcon
        icon="lens"
        class="separator"
      />
      <VueButton
        class="icon-button flat big"
        icon-left="close"
        v-tooltip="'Delete symbol'"
        @click="deleteSymbol()"
      />      
      <VueButton
        class="icon-button flat big"
        icon-left="move"
        v-tooltip="'Move symbol'"
        @click="deleteSymbol()"
      />
      <VueButton
        class="icon-button flat big"
        icon-left="add"
        v-tooltip="'Add wire'"
        @click="deleteSymbol()"
      />
    </div>
  </div>
</template>

<script>

export default {
  methods: {
    selectSymbol (symbolType) {
        // eslint-disable-next-line no-console
        console.log(symbolType)
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~@/style/imports"

.top-bar
  background #CACACA // $vue-ui-color-light
  padding 2px
  h-box()
  align-items center
  position relative
  height 48px
  z-index 1
  box-shadow 0 2px 10px rgba(black, .05)
  .vue-ui-dark-mode &
    background $vue-ui-color-darker
    box-shadow 0 2px 10px rgba(black, .2)

  &,
  .actions
    /deep/ > *
      space-between-x($padding-item)

.custom_width
  width 50px

.vue-ui-empty
  padding 6px

.title
  font-size 22px
  font-weight lighter
</style>
