<template>
  <div>
    <ModalContent @emit-media="pushMedia" />
    <div class="content">
      <div  v-for="el in mediaBlocks" :key="el.id" >
        <AudioContent :src="el.src" v-if="el.type == 'audio'" />
        <VideoContent :src="el.src" v-if="el.type == 'video'" />
        <ImageContent :src="el.src" v-if="el.type == 'image'" />
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
