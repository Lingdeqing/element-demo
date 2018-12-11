<template>
<div>
  <DropSelect v-model="defaultVal"/>
  <div>{{defaultVal}}</div>
  <button @click="setDefault">外部设值</button>
</div>
  
</template>

<script>
import DropSelect from "./_select";
export default {
  name: 'ex-select',
  data: () => ({
    defaultVal: '双皮奶'
  }),
  methods: {
    setDefault(){
      this.defaultVal = '黄金糕'
    }
  },
  components: {
    DropSelect
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
