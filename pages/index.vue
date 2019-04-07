<template>
  <section class="container">
    <div>
      <!-- Memo.vueの中に変数を渡している -->
      <!-- memoInfoListはdata()の返却値な模様 -->
      <!-- addMemoが走るたびに実行されている模様 -->
      <memo
        v-for="(memoInfo, i) in memoInfoList"
        :key="i"
        :posX="memoInfo.posX"
        :posY="memoInfo.posY"
        :text="memoInfo.text"
        @inputed1="setText($event, i)"
        @dragstart="dragText($event, i)"
      />
    </div>
    <add-btn @clicked="addMemo" />
  </section>
</template>

<script>
// indexから見た子供を指定しているっぽい
import Memo from '~/components/Memo.vue'
import AddBtn from '~/components/AddBtn.vue'

// indexから見た子供を指定しているっぽい
export default {
  components: {
    Memo,
    AddBtn
  },
  // 名前変えたらエラーになるから予約語っぽい
  data() {
    return {
      // List自体を複数個指定可能な模様
      memoInfoList: [
        {
          posX: 20,
          posY: 20,
          text: 'tafagawhagta'
        }
      ]
    }
  },
  methods: {
    addMemo() {
      // ブレイクポイント張れないのね。。
      const lastMemo = this.memoInfoList[this.memoInfoList.length - 1]
      // lastMemo[:posX]で要素見れないのは以外。エラーになっちまう。lastMemo.lengthでも見れない。。
      // ああなるほどlastMemo.posXでいけるのね

      // なぜmemoInfoListが入れ子になるのか。
      // 多分、最後の位置に加算しているため
      this.memoInfoList = [
        // ...は意味が分からない
        // よくわからんが、最後のインデックスに存在する値を取り出して、固定値をいれて配列に追加するまでをaddMemoでやっている模様
        // あとは自動でv-forが走って再描画するみたい
        ...this.memoInfoList,
        {
          posX: lastMemo.posX + 220,
          posY: lastMemo.posY + 20,
          text: ''
        }
      ]
    },
    setText(text, i) {
      this.memoInfoList = this.memoInfoList.map((memoInfo, index) => {
        // indexには入力されたMemoの番号がはいる。
        // iはカウンタ。入力Memoと一致した場合、Textを返す
        if (i === index) {
          console.log("i === index")
          console.log(`${i} is if`)
          console.log(`${index} is if`)
          return {
            ...memoInfo,
            text
          }
        } else {
          console.log("i !== index")
          console.log(`${i} is else`)
          console.log(`${index} is else`)
          return memoInfo
        }
      })
    },
    dragText(text, i) {
      console.log('draged')
    },
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background: center/cover url('~assets/background.jpg');
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
