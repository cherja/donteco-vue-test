<template>
  <div class="media">
    <button @click="removeMedia"><img src="../assets/images/close.svg"></button>
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

<style lang="scss">
.media{
  position: relative;
  margin: 10px;
  box-shadow: 0 0 10px 5px #4259b024;
  display: flex;
  justify-content: center;
  align-items: center;
  width:300px;
  height:300px;
  border-radius:3px;

  button {
    position: absolute;
    right: 0;
    top: 0;
    z-index: 1;
     border: none;
    outline: none;
    background: none;
    width: 30px;
    height: 30px;
  }
}
</style>

