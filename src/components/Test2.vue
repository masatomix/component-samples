<template>
  <div>
    <button v-on:click="handle">ボタン</button>
    <input type="text" v-model="param" />
    <div>{{ param }}</div>

    <input type="text" v-model="paramObj.param1" />
    <div>{{ paramObj.param1 }}</div>
  </div>
</template>

<script>
// 値は親コンポーネントで書き換える場合
export default {
  props: {
    param: Number,
    paramObj: Object,
  },
  // data: vm => ({}),
  methods: {
    handle() {
      console.log('親にemitで通知して、親で値を変更させるパタン start')
      // console.log(this.param)
      this.$emit('attack')
      console.log('親にemitで通知して、親で値を変更させるパタン end')
    },
  },
}
</script>
