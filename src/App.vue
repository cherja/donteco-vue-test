<template>
  <div>
    <modalcontent @emit-media="pushMedia"></modalcontent>
    <videocontent></videocontent>
    <audiocontent></audiocontent>
    <imagecontent></imagecontent>
    <ol>
      <li v-for="el in mediaArray" :key="el.id" >{{el}}</li>
    </ol>
  </div> 
</template>

<script>
import audiocontent from './components/Audio.vue'
import videocontent from './components/Video.vue'
import modalcontent from './components/Modal.vue'
import imagecontent from './components/Image.vue'
export default {
  components:{
    audiocontent,
    videocontent,
    modalcontent,
    imagecontent
  },
  data () {
    return {
      mediaArray: []
    }
  },
  methods: {
    pushMedia (e) {
      this.mediaArray.push(e)
    }
  }
}
</script>

<style lang="scss">

</style>
