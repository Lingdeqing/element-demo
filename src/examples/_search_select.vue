<template>
<div>
  <el-select v-model="value1" placeholder="请选择"
    filterable
  >
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.value"
      :value="item.value">
    </el-option>
  </el-select>
  <button @click="setDefault">内部设值</button>
</div>
  
</template>

<script>
export default {
    props: ['value'],
    name: 'i_search-select',
    data() {
        return {
        options: [{
            value: '选项1',
            label: '黄金糕'
        }, {
            value: '选项2',
            label: '双皮奶'
        }, {
            value: '选项3',
            label: '蚵仔煎'
        }, {
            value: '选项4',
            label: '龙须面'
        }, {
            value: '选项5',
            label: '北京烤鸭'
        }],
        value1: ''
        }
    },
    watch: {
        value: {
            immediate: true,
            handler(){
                this.value1 = this.value
            }
        },
        value1(){
            this.$emit('input', this.value1)
        }
    },
    methods: {
        setDefault(){
            this.value1 = '蚵仔煎'
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
