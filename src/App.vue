<template>
  <div>
    <ModalContent @emit-media="pushMedia" />
    <div class="content">
      <div v-for="el in mediaBlocks" :key="el.id" >
        <AudioContent @emit-id="removeMedia" :src="el.src" :id="el.id" v-if="el.type == 'audio'" />
        <VideoContent @emit-id="removeMedia" :src="el.src" :id="el.id" v-if="el.type == 'video'" />
        <ImageContent @emit-id="removeMedia" :src="el.src" :id="el.id" v-if="el.type == 'image'" />
      </div>
    </div>

  </div> 
</template>

<script>
import AudioContent from './components/Audio.vue'
import VideoContent from './components/Video.vue'
import ModalContent from './components/Modal.vue'
import ImageContent from './components/Image.vue'

export default {
  components:{
    AudioContent,
    VideoContent,
    ModalContent,
    ImageContent
  },
  data () {
    return {
      mediaBlocks: [
      ],
      increment: 0
    }
  },
  methods: {
    pushMedia (e) {
      let id = this.increment ++
      e.id = id
      this.mediaBlocks.push(e)
    },
    removeMedia(e) { 
      this.mediaBlocks = this.mediaBlocks.filter(item => item.id !== e)
    }
  }
}
</script>

<style lang="scss">
.content {
  display: flex;
  flex-wrap: wrap;
}
</style>
