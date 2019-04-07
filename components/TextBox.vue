<template>
  <textarea
    class="text-box"
    :value="text"
    @input="onInput"
  />
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    }
  },
  // index.vueのinputedを発火させているみたいだが、なぜMemoにも必要なのか。
  // わかった。TextBoxではMemoのinputed1に繋がっている模様。
  methods: {
    onInput(e) {
      console.log("TextBox onInput")
      this.$emit('inputed1', e.target.value)
    }
  }
}
</script>

<style>
.text-box {
  position: absolute;
  display: block;
  bottom: 0;
  top: 60px;
  left: 0;
  width: 100%;
  background: transparent;
}
</style>
