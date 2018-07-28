<template>
   <div v-html="htmlData">
   </div>
</template>
<script>
import axios from 'axios'

export default {
    name: 'NavIntro',    
    props: {
        src: {
            type: String
        }
    },
    data() {
        return {
            baseUrl: process.env.BASE_URL,
            htmlData: "",
            loaded: false,
            error: false
        }
    },
    mounted() {
        this.readHtmlData()
    },
    methods: {
        readHtmlData() {
            var self = this
            axios.get(`${this.baseUrl}or_gate.html`).then(response => {
                self.htmlData = response.data
            })
        }        
    }
};
</script>

<style lang="stylus" scoped>
@import "~@/style/imports"

.nav-intro
  overflow-x hidden
  overflow-y auto
  background $color-background-light
  .vue-ui-dark-mode &
    background lighten($vue-ui-color-darker, 1%)
</style>
