<template>
  <div>
    <button @click="removeMedia">delete</button>
    <AudioContent  :src="el.src" v-if="el.type == 'audio'" />
    <VideoContent  :src="el.src" v-if="el.type == 'video'" />
    <ImageContent  :src="el.src" v-if="el.type == 'image'" />
  </div>
</template>

<script>

import VideoContent from './Video.vue'
import AudioContent from './Audio.vue'

import ImageContent from './Image.vue'

export default {
    components:{
     AudioContent,
     VideoContent,
     ImageContent
  },

  props: {
    el: {
      type: Object,
      required: true
    }
  },
   methods: {
    removeMedia() {
      this.$emit('emit-id', this.el.id )
    }
  }
}
</script>
