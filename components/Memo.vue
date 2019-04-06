<template>
  <div
    :style="{
      left: `${posX}px`
    }"
    class="memo">
  </div>
</template>

<script>
export default {
  props: {
    posX: {
      type: Number,
      required: true
    }
  }
}
</script>

<style>
.memo {
  position: fixed;
  top: 20px;
  width: 200px;
  height: 300px;
  background: #ff0;
}
</style>