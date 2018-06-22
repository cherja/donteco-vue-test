<template>
  <div class="app">
    <button @click="modalWindow = true">
      <span>Добавить медиа</span>
    </button>
    <div class="app-modal-window" v-if="modalWindow"> 
        <P>
          <input type="radio" name="test" id="audio" value="audio">
          <label for="audio">Аудио</label>
        </P>
        <P>
          <input type="radio" name="test" id="video" value="video">
          <label for="video">Видео</label>
        </P>
        <P>
          <input type="radio" name="test" id="image" value="image">
          <label for="image">Изображение</label>
        </P>
        <P>
          <label for="src">Путь</label>
          <input type="text" name="test" id="src">
        </P>
      <button class="app-modal-window_close" @click="modalWindow = false">х</button>
      <button @click="addMedia()">Добавить</button>   
    </div>
  </div>

</template>

<script>
export default {
  data () {
    return {
      modalWindow: false
    }
  },
  methods: {
    addMedia() {
      this.$emit('emit-media', `<audiocontent></audiocontent>`)
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
