<template>
  <div class="audio-box">
    <audio 
      controls
      :src="src">
    </audio>
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
.audio-box{
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 10px;
  width:300px;
  height:300px;
  border: 1px solid #000;
  border-radius:3px;
}
</style>