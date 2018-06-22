<template>
  <div>
    <modalcontent></modalcontent>
    <videocontent></videocontent>
    <audiocontent></audiocontent>
    <imagecontent></imagecontent>
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
  }
}
</script>

<style lang="scss">

</style>
