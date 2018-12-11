<template>
<div>
  <Select v-model="defaultVal"/>
  <div>{{JSON.stringify(defaultVal)}}</div>
  <button @click="setDefault">外部设值</button>
</div>
  
</template>

<script>
import Select from "./_group_search_object_select2";
export default {
  name: 'ex-select-object',
  data: () => ({
    defaultVal: [{
        value: '选项1',
        label: '黄金糕'
    }]
  }),
  methods: {
    setDefault(){
      this.defaultVal = [{
            value: '选项1',
            label: '黄金糕'
        }, {
            value: '选项3',
            label: '蚵仔煎'
        }]
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
