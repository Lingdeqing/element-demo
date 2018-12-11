<template>
  <div id="app">
    <el-row>
      <el-col :span="4">
        <ul>
          <li><router-link to="/transition">过度</router-link></li>
          <li><router-link to="/layout">布局</router-link></li>
          <li><router-link to="/select">下拉选择(双向绑定)</router-link></li>
          <li><router-link to="/searchselect">下拉选择(搜索)</router-link></li>
          <li><router-link to="/searchobjectselect">下拉选择(搜索对象)</router-link></li>
          <li><router-link to="/multisearchobjectselect">下拉选择(多选 搜索对象)</router-link></li>
          <li><router-link to="/groupsearchobjectselect">下拉选择(分组 搜索对象)</router-link></li>
          <li><router-link to="/groupsearchobjectselect2">下拉选择(分组 搜索对象 传入对象 陷入死循环啊...)</router-link></li>
          <li><router-link to="/datepicker">日历</router-link></li>
        </ul>
      </el-col>
      <el-col :span="20">
        <router-view></router-view>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import Vue from 'vue'
import VueRouter from 'vue-router'

import transition from './examples/transition.vue'
import layout from './examples/layout.vue'
import select from './examples/select.vue'
import searchselect from './examples/search_select.vue'
import searchobjectselect from './examples/search_object_select.vue'
import multisearchobjectselect from './examples/multi_search_object_select.vue'
import groupsearchobjectselect from './examples/group_search_object_select.vue'
import groupsearchobjectselect2 from './examples/group_search_object_select2.vue'
import datepicker from './examples/datepicker.vue'

Vue.use(VueRouter);

export default {
  name: 'app',
  router: new VueRouter({
    routes: [
      { path: '/', redirect: '/datepicker'},
      { path: '/transition', component: transition},
      { path: '/layout', component: layout},
      { path: '/select', component: select},
      { path: '/searchselect', component: searchselect},
      { path: '/searchobjectselect', component: searchobjectselect},
      { path: '/multisearchobjectselect', component: multisearchobjectselect},
      { path: '/groupsearchobjectselect', component: groupsearchobjectselect},
      { path: '/groupsearchobjectselect2', component: groupsearchobjectselect2},
      { path: '/datepicker', component: datepicker},
    ]
  })
}
</script>

<style scoped>
a{margin-right: 10px;}
.router-link-active{color: red;}
</style>
