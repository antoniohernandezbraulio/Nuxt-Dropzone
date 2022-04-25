<template>
  <v-row>
    <v-col class="text-center">
        <dropzone id="foo" ref="el" :options="options" :destroyDropzone="true" v-on:vdropzone-sending="sendingEvent"></dropzone>
    </v-col>
  </v-row>
</template>

<script>
import Dropzone from 'nuxt-dropzone'
import 'nuxt-dropzone/dropzone.css'
 
export default {
  components: {
    Dropzone
  },
  data() {
    return {
      options: {
        url: "http://httpbin.org/anything"
      }
    }
  },
  methods:{
    sendingEvent(file, xhr, formData){
      formData.append("uploads",file,file.name)
      this.$refs.el.removeAllFiles()
    }
  },
  mounted() {
    const instance = this.$refs.el.dropzone
  }
}
</script>