<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-container"> 
        <P>
          <input 
            type="radio"
            id="audio" 
            value="audio" 
            v-model="type" 
          >
          <label for="audio">Аудио</label>
        </P>
        <P>
          <input 
            type="radio"                            
            id="video" 
            value="video" 
            v-model="type" 
          >
          <label for="video">Видео</label>
        </P>
        <P>
          <input 
            type="radio" 
            id="image" 
            value="image" 
            v-model="type" 
          >
          <label for="image">Изображение</label>
        </P>
        <P>
          <label for="src">Путь</label>
          <input id="src" v-model="src">
        </P>
        <button class="modal-container__close" @click="$emit('close')">
          <img src="../assets/images/exit.svg">
        </button>
        <button class="modal-container__add" @click="addMedia">
          <img src="../assets/images/add.svg">
        </button>   
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data () {
    return {
      type: 'audio',
      src: ''        
    }
  },
  methods: {
    addMedia() {
      if(this.src === '') {
        if(this.type === 'audio') {
          this.src = 'https://m.vk.com/mp3/audio_api_unavailable.mp3'
        }else if (this.type === 'video') {
         this.src = 'https://cs529306.vkuservideo.net/u223412927/videos/fd5a982178.720.mp4?extra=ru_pYFsedoBvH78r6t3BH7XjYDL15bcYLX4kCOICgEymDSLxr8iMeTflt_F5isu5CCJ2YVYZj3HLGK32KGGZ5j0UPVoiePY4OjRv527ESvwY9EUrDEIoGWTr2Ua-mXBbPgbIpuucUA'
        }else {
          this.src = 'http://www.1gai.ru/uploads/posts/2014-10/1414425445_mercedes-benz-s550-coupe-8.jpg'
        }  
      }
      this.$emit('emit-media', { type: this.type, src: this.src })
    }
  }
}
</script>

<style lang="scss">
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: opacity .3s ease;
}

.modal-container {
  position: relative;
  width: 400px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;

  img {
    width: 24px;
    height: 24px;
  }

  &__close, &__add {
    border: none;
    outline: none;
    background: none;
    position: absolute;
    padding: 5px 5px;
  }

  &__close {
    right: 0;
    top:0;
  }

  &__add {
    right: 0;
    bottom:0;
  }
}

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
