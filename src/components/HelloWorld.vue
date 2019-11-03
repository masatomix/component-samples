<template>
  <div class="hello">
    <!-- https://jp.vuejs.org/v2/guide/components-custom-events.html#sync-%E4%BF%AE%E9%A3%BE%E5%AD%90 -->
    <h2>子で値を変更パタン(.sync版)(Test.vue)</h2>
    <Test :param.sync="p1" :paramObj.sync="p2"></Test>
    [{{ p1 }}] [{{ p2 }}]

    <!-- .syncの書き方は、下記バージョンのsyntactic sugarといえる -->
    <h2>子で値を変更パタン(.sync未使用パタン)(Test.vue)</h2>
    <Test
      :param="p1"
      :paramObj="p2"
      @update:param="p1 = $event"
      @update:paramObj="p2 = $event"
    ></Test>
    [{{ p1 }}] [{{ p2 }}]
    <hr />

    <h2>親にemitで通知して、親で値を変更させるパタン(Test2.vue)</h2>
    <Test2 :param="p3" :paramObj="p4" @attack="aMethod"></Test2>
    [{{ p3 }}] [{{ p4 }}]
    <hr />

    <h2>v-model(syntactic sugarナシバージョン)(Test3.vue)</h2>
    <Test3 :value="p5" @input="p5 = $event"></Test3>
    [{{ p5 }}]

    <h2>v-model(syntactic sugarバージョン)(Test3.vue)</h2>
    <Test3 v-model="p5"></Test3>
    [{{ p5 }}]
    <hr />

    <h2>v-model(Objectの場合)(Test4.vue)</h2>
    <Test4 :value="p6" @input="p6 = $event"></Test4>
    [{{ p6.param1 }}]

    <h2>v-model(Objectの場合)(Test4.vue)</h2>
    <Test4 v-model="p6"></Test4>
    [{{ p6.param1 }}]
    <hr />
  </div>
</template>

<script>
// https://jp.vuejs.org/v2/guide/components.html
import Test from './Test.vue'
import Test2 from './Test2.vue'
import Test3 from './Test3.vue'
import Test4 from './Test4.vue'

export default {
  name: 'HelloWorld',
  components: {
    Test,
    Test2,
    Test3,
    Test4,
  },
  data: () => ({
    p1: 1,
    p2: { param1: 2 },

    p3: 3,
    p4: { param1: 4 },
    p5: 5,
    p6: { param1: 6 },
  }),
  methods: {
    aMethod() {
      this.p3 += 3
      this.p4.param1 -= 3
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
