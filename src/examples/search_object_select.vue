<template>
<div>
  <Select v-model="defaultVal"/>
  <div>{{defaultVal}}</div>
  <button @click="setDefault">外部设值</button>
</div>
  
</template>

<script>
import Select from "./_search_object_select";
export default {
  name: 'ex-select-object',
  data: () => ({
    defaultVal: '选项1'
  }),
  methods: {
    setDefault(){
      this.defaultVal = '选项1'
    }
  },
  components: {
    Select
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
