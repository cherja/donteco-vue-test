<template>
  <div class="video-box"> 
      <video 
      controls
      :src="src">
    </video>
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss">
.video-box {
  margin: 10px;
  width:300px;
  height:300px;
  border: 1px solid #000;
  border-radius:3px;
}
</style>