<template>
  <div>
    <button class="open-modal" @click="isShow = true">Добавить медиа</button>
    <ModalContent 
      @emit-media="pushMedia" 
      @close="isShow = false" 
      v-if="isShow" 
    >  
      <img src="./assets/images/add.svg">
    </ModalContent>  
    <draggable 
      class="content" 
      :options="{group:'people'}"
      @start="drag=true" 
      @end="drag=false">
        <MediaContent 
          @emit-id="removeMedia" 
          v-for="el in mediaBlocks" 
          :el="el" 
          :key="el.id"
        />  
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
      isShow:      false,
      mediaBlocks: [],
      increment:   0
    }
  },
  methods: {
    pushMedia (e) {
      let id = this.increment ++
      e.id = id
      this.mediaBlocks.push(e)
      this.isShow = false
    },
    removeMedia(e) { 
      this.mediaBlocks = this.mediaBlocks.filter(item => item.id !== e)
    }
  }
}
</script>

<style lang="scss">
@font-face {
  font-family: "SF";
  font-weight: normal;
  src: url("assets/fonts/SFUIDisplay-Regular.woff");
}

$primary-color: #27ae60;

* {
  font-family: "SF";
  letter-spacing: .08em;
  font-weight: 800;
}

body {
  background-color: #08AEEA;
  background-image: linear-gradient(90deg, #08AEEA 0%, #2AF598 100%);
}

button {
  cursor: pointer;
}

.content {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.open-modal { 
  outline: none;
  text-align: center;
  border: none;
  margin: 5px 5px;
  background: $primary-color;
  color: #fff;
  letter-spacing: 2px;
  font-size: 15px;
  padding: .7em 1em;
  border-radius: 40px;
  transition: all 0.3s;
}

.open-modal:hover {
  background: darken($primary-color,10%);
  transform: scale(1.1);
}
</style>
