<template>
  <div class="app">
    <button @click="isShow = true">
      <span>Добавить медиа</span>
    </button>
    <div class="app-modal-window" v-if="isShow"> 
        <P>
          <input v-model="type" type="radio" id="audio" value="audio" >
          <label for="audio">Аудио</label>
        </P>
        <P>
          <input v-model="type" type="radio" id="video" value="video" >
          <label for="video">Видео</label>
        </P>
        <P>
          <input v-model="type" type="radio" id="image" value="image" >
          <label for="image">Изображение</label>
        </P>
        <P>
          <label for="src">Путь</label>
          <input v-model="src" id="src">
        </P>
      <button class="app-modal-window_close" @click="isShow = false">х</button>
      <button @click="addMedia">Добавить</button>   
    </div>
  </div>

</template>

<script>
export default {
  data () {
    return {
      isShow      : false,
      type        : 'audio',
      src         : ''        
    }
  },
  methods: {
    addMedia() {
      this.$emit('emit-media', { type:this.type, src:this.src } )
    }
  }
}
</script>

<style lang="scss">
.app {
  height: 220px;

  &-modal-window{
    position: fixed;
    left:0;
    right:0;
    margin: auto;
    width: 300px;
    box-shadow: 0 0 40px rgba(0, 0, 0, .1) inset; 
    z-index: 1;

    &_close{
      border: none;
      outline: none;
      background: none;
      position: absolute;
      top: 0px;
      right: 0px;
      width: 20px;
      height: 20px;
    }
  }
}
</style>
