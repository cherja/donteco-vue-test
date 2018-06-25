<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container"> 
          <P>
            <input 
              v-model="type" 
              type="radio" 
              id="audio" 
              value="audio" 
            >
            <label for="audio">Аудио</label>
          </P>
          <P>
            <input 
              v-model="type" 
              type="radio" 
              id="video" 
              value="video" 
            >
            <label for="video">Видео</label>
          </P>
          <P>
            <input 
              v-model="type" 
              type="radio" 
              id="image" 
              value="image" 
            >
            <label for="image">Изображение</label>
          </P>
          <P>
            <label for="src">Путь</label>
            <input v-model="src" id="src">
          </P>
          <button class="modal-container__close" @click="$emit('close')">х</button>
          <button @click="addMedia">Добавить</button>   
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data () {
    return {
      type: 'audio',
      src:  ''        
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
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
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

  &__close {
    border: none;
    outline: none;
    background: none;
    position: absolute;
    right: 0;
    top:0;
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
