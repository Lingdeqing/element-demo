<template>
<div>
  <el-select v-model="value1" placeholder="请选择"
    filterable
    default-first-option
    :filter-method="query"
    value-key="value"
  >
    <el-option
      v-for="item in options"
      v-if="item.visible"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>
  <button @click="setDefault">内部设值</button>
</div>
  
</template>

<script>

const table = [{
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
                }];
table.forEach((item) => {
    item.visible = true;
})


export default {
    props: ['value'],
    name: 'i_search-object-select',
    data() {
        return {
        options: table,
        value1: ''
        }
    },
    watch: {
        value: {
            immediate: true,
            handler(){
                this.value1 = this.value;
            }
        },
        value1(){
            this.$emit('input', this.value1)
        }
    },
    methods: {
        setDefault(){
            this.value1 = '选项2'
        },
        query(keywords){
            this.options.forEach((item) => {
                if(keywords && item.value.indexOf(keywords) > -1){
                    item.visible = true;
                } else {
                    item.visible = false;
                }
            })
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
