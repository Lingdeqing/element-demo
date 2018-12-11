<template>
<div>
  <el-select v-model="value1" placeholder="请选择"
    filterable
    default-first-option
    multiple
    :filter-method="query"
    value-key="value"
  >
    <el-option-group
      v-for="group in groups"
      v-if="group.visible"
      :key="group.value"
      :label="group.label">
        <el-option
        v-for="item in group.options"
        v-if="item.visible"
        :key="item.value"
        :label="item.label"
        :value="item.value">
        </el-option>
    </el-option-group>
  </el-select>
  <button @click="setDefault">内部设值</button>
</div>
  
</template>

<script>

const groups = [{
    value: '分组1',
    label: '分组1',
    options: [
        {
            value: '选项1',
            label: '黄金糕'
        }, {
            value: '选项2',
            label: '双皮奶'
        }
    ]
}, {
    value: '分组2',
    label: '分组2',
    options: [
        {
            value: '选项3',
            label: '蚵仔煎'
        }, {
            value: '选项4',
            label: '龙须面'
        }, {
            value: '选项5',
            label: '北京烤鸭'
        }
    ]
}];
const optionMap = {};

groups.forEach((group) => {
    group.visible = true;
    group.options.forEach((item) => {
        item.visible = true;
        optionMap[item.value] = item;
    })
})


export default {
    props: ['value'],
    name: 'i_search-object-select',
    data() {
        return {
        groups: groups,
        value1: []
        }
    },
    watch: {
        value: {
            immediate: true,
            deep: false,
            handler(){
                this.value1 = this.value.map((item) => item.value);
            }
        },
        value1(){
            this.$emit('input', this.value1.map(value => optionMap[value]))
        }
    },
    methods: {
        setDefault(){
            // this.value1 = ['选项1', '选项2']
        },
        query(keywords){
            this.groups = this.groups.map((group) => {
                let groupVisible = false;
                group.options.forEach((item) => {
                    if(keywords && item.value.indexOf(keywords) > -1){
                        item.visible = true;
                        groupVisible = true;
                    } else {
                        item.visible = false;
                    }
                })
                group.visible = groupVisible;
                return group;
            });
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
