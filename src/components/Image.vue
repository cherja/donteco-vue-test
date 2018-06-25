<template>
  <div class="img-box">
      <img :src="src" alt="Изображение">
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
.img-box{
    position: relative;
    width:300px;
    height:300px;
    
    img{
      position: absolute;
      left:50%;
      top:50%;
      transform: translate(-50%, -50%);
      max-width:100%;
      max-height: 100%;
    }
}
</style>

