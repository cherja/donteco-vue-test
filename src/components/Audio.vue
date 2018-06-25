<template>
  <div class="audio-box">
    <audio controls :src="src">
    </audio>
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type:     String,
      required: true
    }
  }
}
</script>
