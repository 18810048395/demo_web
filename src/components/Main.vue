<template>
  <el-container style="border: 1px solid #eee">
    <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
      <el-menu :default-openeds="['1', '3']">
        <el-submenu index="1">
          <template slot="title"
            ><i class="el-icon-menu"></i>个人中心</template
          >
          <el-menu-item-group>
            <!-- <template slot="title">分组一</template> -->
            <el-menu-item index="1-1">用户列表</el-menu-item>
            <!-- <el-menu-item index="1-2">选项2</el-menu-item> -->
          </el-menu-item-group>
          <!-- <el-menu-item-group title="分组2">
            <el-menu-item index="1-3">选项3</el-menu-item>
          </el-menu-item-group> -->
          <!-- <el-submenu index="1-4">
            <template slot="title">选项4</template>
            <el-menu-item index="1-4-1">选项4-1</el-menu-item>
          </el-submenu> -->
        </el-submenu>
        <!-- <el-submenu index="2">
          <template slot="title"><i class="el-icon-message"></i>导航二</template>
          <el-menu-item-group>
            <template slot="title">分组一</template>
            <el-menu-item index="2-1">选项1</el-menu-item>
            <el-menu-item index="2-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="2-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="2-4">
            <template slot="title">选项4</template>
            <el-menu-item index="2-4-1">选项4-1</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title"
            ><i class="el-icon-setting"></i>导航三</template
          >
          <el-menu-item-group>
            <template slot="title">分组一</template>
            <el-menu-item index="3-1">选项1</el-menu-item>
            <el-menu-item index="3-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="3-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="3-4">
            <template slot="title">选项4</template>
            <el-menu-item index="3-4-1">选项4-1</el-menu-item>
          </el-submenu>
        </el-submenu> -->
      </el-menu>
    </el-aside>

    <el-container>
      <el-header style="text-align: right; font-size: 15px">
        <button @click="logOut()" >退出</button>
        <!-- <el-dropdown>
          <i class="el-icon-setting" style="margin-right: 15px"></i>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>查看</el-dropdown-item>
             <el-dropdown-item>新增</el-dropdown-item>
            <el-dropdown-item>删除</el-dropdown-item> 
          </el-dropdown-menu>
        </el-dropdown> -->
      </el-header>

      <el-main>
        <el-table :data="tableData">
          <el-table-column prop="userName" label="姓名" width="150">
          </el-table-column>
          <el-table-column prop="userSex" label="性别" width="150">
          </el-table-column>
          <el-table-column prop="userAddress" label="地址"> </el-table-column>
        </el-table>
      </el-main>
    </el-container>
  </el-container>
</template>


<script>
import {getUserList} from '../axios/api.js'
export default {
  data() {
    return {
      tableData: [],
    };
  },
  methods: {
    getAllUser(){
      getUserList().then((result) => {
        this.tableData = result.data;
      } )
    },
    logOut(){
      console.log("logOut")
      this.$router.push('/');
    }
    
  },
  mounted(){
     this.getAllUser();
  }
  
};
</script>

<style>
.el-header {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
</style>

