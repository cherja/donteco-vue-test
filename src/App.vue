<template>
  <div>
    <button class="open-modal" @click="isShow = true">Добавить медиа</button>
    <ModalContent 
      v-if="isShow" 
      @emit-media="addMedia" 
      @close="isShow = false" 
    />  
    <draggable class="content">
      <div
        v-for="(block, i) in mediaBlocks"
        :key="i"
        class="media"
      >
        <button class="media__close" @click="removeMedia(i)">
          <img src="./assets/images/close.svg">
        </button>
        <audio v-if="block.type === 'audio'" :src="block.src" controls />
        <video v-if="block.type === 'video'" :src="block.src" controls />
        <img v-if="block.type === 'image'" :src="block.src" alt="Изображение" />
      </div>
    </draggable>
  </div> 
</template>

<script>
import ModalContent from './components/Modal.vue'
import draggable from 'vuedraggable'

export default {
  components:{
    ModalContent,
    draggable
  },
  data () {
    return {
      isShow:      false,
      mediaBlocks: []
    }
  },
  methods: {
    addMedia (mediaBlock) {
      this.mediaBlocks.push(mediaBlock)
      this.isShow = false
    },
    removeMedia (index) {
      this.mediaBlocks.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" src="./styles.scss"></style>
