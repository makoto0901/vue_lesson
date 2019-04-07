<template>
<!-- ※※※※※※※※※質問事項※※※※※※※※※-->
<!-- このDOMでdrag関連のイベントをトラップしてMemo.vueに値を渡そうと考えています。 -->
<!-- 
しかし、以下イベントを全て試したのですがイベントが発火しませんでした。
@dragstart
@dragenter
@dragleave
@dragover
@dragend。 
-->
<!-- @clickが発火するので方針としては間違っていないと思うのですが、指定するイベント名が異なるのでしょうか。 -->
  <div class="drag-handler" 
  @click="draged"
  />
</template>

<script>
export default {
  methods: {
    draged(e) {
      console.log('draged')
    }
  }
}
</script>

<style>
.drag-handler {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  cursor: pointer;
}
</style>
