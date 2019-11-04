<template>
  <div>
    <button v-on:click="handle">ボタン</button>
    <input type="text" v-model="localParam" />
    <div>{{ localParam }}</div>

    <input type="text" v-model="localParamObj.param1" />
    <div>{{ localParamObj.param1 }}</div>
  </div>
</template>

<script>
// 値をこちらのコンポーネントで書き換える場合
export default {
  props: {
    param: Number,
    paramObj: Object,
  },
  computed: {
    localParam: {
      get: function() {
        return this.param
      },
      set: function(value) {
        this.$emit('update:param', value)
      },
    },
    localParamObj: {
      get: function() {
        return this.paramObj
      },
      set: function(value) {
        this.$emit('update:paramObj', value)
      },
    },
  },
  // data: vm => ({}),
  methods: {
    handle() {
      console.log('syncを使って、子で値を変更パタン start')
      this.localParam -= 1
      this.localParamObj.param1 += 1
      console.log('syncを使って、子で値を変更パタン end')
    },
  },
}
</script>
