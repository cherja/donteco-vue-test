<template>
  <div class="audio-box">
    <audio 
      controls
      :src="src" :id="id">
    </audio>
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