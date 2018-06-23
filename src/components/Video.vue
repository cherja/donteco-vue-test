<template>
  <div class="video-box"> 
      <video 
      controls
      :src="src">
    </video>
    <button @click="removeMedia">delete</button>
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      required: true
    },
    id: {
      type: Number,
      required: true
    }
  },
   methods: {
    removeMedia() {
      this.$emit('emit-id', this.id )
    }
  }
}
</script>

<style lang="scss">
.video-box {
    margin: 10px;
    position: relative;
    width:300px;
    height:300px;
    background: #c2c2c2;
    border: 1px solid #000;
    border-radius:3px;

    video {
      position: absolute;
      left:50%;
      top:50%;
      transform: translate(-50%, -50%);
      max-width:100%;
      max-height: 100%;
    }
}
</style>