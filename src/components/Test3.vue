<template>
  <div>
    <button v-on:click="handle">ボタン</button>
    <input type="text" v-model="localParam" />
    <div>{{ localParam }}</div>
  </div>
</template>

<script>
// 値をこちらのコンポーネントで書き換える場合
export default {
  props: {
    value: Number,
  },
  computed: {
    localParam: {
      get: function() {
        return this.value
      },
      set: function(value) {
        this.$emit('input', value) // おやでは @input に書いたメソッドがよばれる。引数にvalue
      },
    },
  },
  // data: vm => ({}),
  methods: {
    handle() {
      console.log('v-modelバージョン start')
      console.log(this.localParam)
      this.localParam += 10 // 実際は、うえのsetterが呼ばれてemitされる
      console.log(this.localParam)
      console.log('v-modelバージョン  end')
    },
  },
}
</script>
