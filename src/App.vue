<script setup lang="ts">
import { ref } from 'vue'
import orgApi from './api/org'
import userApi from './api/user'
import type { TabsPaneContext } from 'element-plus'
import { Plus } from '@element-plus/icons-vue'
import OrgTree from './components/OrgTree.vue'

const activeName = ref('first')



const handleClick = (tab: TabsPaneContext, event: Event) => {
  console.log(tab, event)
}
userApi.query({}).then((users) => {
  console.log(users)
})


</script>

<template>
    <el-tabs v-model="activeName" class="demo-tabs" @tab-click="handleClick">
        <el-tab-pane label="成员管理" name="first">
            <div class="common-layout">
                <el-container style="height: 100vh;">
                  <el-aside width="200px">
                    <div class="aside-header">
                      <span>部门</span>
                      <el-button :icon="Plus" text />
                    </div>
                    <OrgTree />
                    
                  </el-aside>
                  <el-main>
                    <div class="main-header">
                      <el-breadcrumb separator="/">
                        <el-breadcrumb-item :to="{ path: '/' }">厦门嗨行旅游</el-breadcrumb-item>
                        <el-breadcrumb-item>技术部</el-breadcrumb-item>
                      </el-breadcrumb>
                    </div>
                  </el-main>
                </el-container>
            </div>
        </el-tab-pane>
        <el-tab-pane label="团队管理" name="second">团队管理</el-tab-pane>
        <el-tab-pane label="职位维护" name="third">职位维护</el-tab-pane>
    </el-tabs>
</template>

<style scoped>
.demo-tabs > .el-tabs__content {
  padding: 32px;
  color: #6b778c;
  font-size: 32px;
  font-weight: 600;
}

.aside-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;
  padding: 0 12px;
  border-bottom: 1px solid #eee;
  border-right: 1px solid #eee;
}

.main-header {
  border-bottom: 1px solid #eee;
  height: 40px;
  display: flex;
  align-items: center;
  padding: 0 12px;
}

.el-aside {
  height: 100% !important;
  border-right: 1px solid #eee;
}
.el-main {
  padding: 0 !important;
}
</style>