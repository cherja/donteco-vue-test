<template>
  <div>
    <ModalContent @emit-media="pushMedia" />
    <div class="content">
      <div v-for="el in mediaBlocks" :key="el.id">
        <MediaContent @emit-id="removeMedia" :el="el">
        </MediaContent>
      </div>
    </div>
  </div> 
</template>

<script>
import ModalContent from './components/Modal.vue'
import MediaContent from './components/Media.vue'

export default {
  components:{
    ModalContent,
    MediaContent
  },
  data () {
    return {
      mediaBlocks: [],
      increment  : 0
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
