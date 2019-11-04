<template>
  <div>
    <h2>対応策1(OkComponent1.vue)</h2>
    <OkComponent1 :value="param1" @input="param1 = $event"></OkComponent1>
    [{{ param1 }}]

    <h2>対応策1(のsyntactic sugarバージョン)(OkComponent1.vue)</h2>
    <OkComponent1 v-model="param1"></OkComponent1>
    [{{ param1 }}]
    <hr />

    <h2>Objectでも、OK(OkComponent11.vue)</h2>
    <OkComponent11 :value="param2" @input="param2 = $event"></OkComponent11>
    [{{ param2 }}]
    <h2>そのsyntactic sugar版(OkComponent11.vue)</h2>
    <OkComponent11 v-model="param2"></OkComponent11>
    [{{ param2 }}]
    <hr />

    <!-- https://jp.vuejs.org/v2/guide/components-custom-events.html#sync-%E4%BF%AE%E9%A3%BE%E5%AD%90 -->
    <!-- .syncの書き方は、下記バージョンのsyntactic sugarといえる -->
    <h2>複数パラメタを渡すパタン(.sync未使用パタン)(OkComponent2.vue)</h2>
    <OkComponent2
      :param="param1"
      :paramObj="param2"
      @update:param="param1 = $event"
      @update:paramObj="param2 = $event"
    ></OkComponent2>
    [{{ param1 }}] [{{ param2 }}]

    <h2>それとほぼ等価な.sync版(OkComponent2.vue)</h2>
    <OkComponent2 :param.sync="param1" :paramObj.sync="param2"></OkComponent2>
    [{{ param1 }}] [{{ param2 }}]
    <hr />

    <h2>番外:親にemitで通知して、親で値を変更させるパタン(Test2.vue)</h2>
    <OkComponent3
      :param="param3"
      :paramObj="param4"
      @attack="aMethod"
    ></OkComponent3>
    [{{ param3 }}] [{{ param4 }}]
    <hr />
  </div>
</template>

<script>
// https://jp.vuejs.org/v2/guide/components.html
import OkComponent1 from './OkComponent1.vue'
import OkComponent11 from './OkComponent11.vue'
import OkComponent2 from './OkComponent2.vue'
import OkComponent3 from './OkComponent3.vue'

export default {
  name: 'HelloWorld',
  components: {
    OkComponent1,
    OkComponent11,
    OkComponent2,
    OkComponent3,
  },
  data: () => ({
    param1: 1,
    param2: { param1: 2 },
    param3: 3,
    param4: { param1: 4 },
  }),
  methods: {
    aMethod() {
      this.param3 += 3
      this.param4.param1 -= 3
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
