<template>
  <div class="video-box"> 
      <video 
      controls
      :src="src"
      class="video-box__video"
    />
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type:     String,
      required: true
    }
  }
}
</script>

<style lang="scss">
.video-box {
    position: relative;
    width:300px;
    height:300px;
    
    &__video {
      position: absolute;
      left:50%;
      top:50%;
      transform: translate(-50%, -50%);
      max-width:100%;
      max-height: 100%;
    }
}
</style>