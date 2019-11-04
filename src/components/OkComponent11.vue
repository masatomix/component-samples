<template>
  <div>
    <button v-on:click="handle">ボタン</button>
    [<input type="text" v-model="localValue.param1" />]
    <div>{{ localValue.param1 }}</div>
  </div>
</template>

<script>
// 値をこちらのコンポーネントで書き換える場合
export default {
  props: {
    value: Object,
  },
  computed: {
    localValue: {
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
      console.log(this.localValue)
      this.localValue.param1 += 10
      console.log(this.localValue)
      console.log('v-modelバージョン end')
    },
  },
}
</script>
