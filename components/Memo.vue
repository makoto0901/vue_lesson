<template>
  <div
    :style="{
      top: `${posY}px`,
      left: `${posX}px`
    }"
    class="memo">
    <drag-handler />
    <text-box
      :text="text"
      @inputed1="onInputed" />
  </div>
</template>

<script>
import DragHandler from '~/components/DragHandler.vue'
import TextBox from '~/components/TextBox.vue'

export default {
  components: {
    DragHandler,
    TextBox
  },
  props: {
    posX: {
      type: Number,
      required: true
    },
    posY: {
      type: Number,
      required: true
    },
    text: {
      type: String,
      required: true
    }
  },
  methods: {
    onInputed(text) {
          console.log("Memo onInputed")
      this.$emit('inputed1', text)
    }
  }
}
</script>

<style>
.memo {
  position: fixed;
  width: 200px;
  height: 300px;
  background: #ff0;
}
</style>
