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
    margin: 10px;
    position: relative;
    width:300px;
    height:300px;
    background: #c2c2c2;
    border: 1px solid #000;
    border-radius:3px;

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

