<template>
  <div>
    <button @click="isShow = true">
      <span>Добавить медиа</span>
    </button>
    <ModalContent @emit-media="pushMedia" @close="isShow = false" v-if="isShow" />    
    <draggable class="content" v-model="myArray" :options="{group:'people'}" @start="drag=true" @end="drag=false">
      <div v-for="el in mediaBlocks" :key="el.id">
        <MediaContent @emit-id="removeMedia" :el="el" />
      </div>
    </draggable>
  </div> 
</template>

<script>
import ModalContent from './components/Modal.vue'
import MediaContent from './components/Media.vue'
import draggable from 'vuedraggable'

export default {
  components:{
    ModalContent,
    MediaContent,
    draggable
  },
  data () {
    return {
      isShow      : false,
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
