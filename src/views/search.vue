<template>
  <div class="box">
    <el-row>
      <el-col :span="12" :offset="6">
        <el-input v-model="search" placeholder="请输入名称" suffix-icon="el-icon-search"></el-input>
      </el-col>
      <el-col :span="24">
        <div class="list" v-if="newUsers.length">
          <div class="item" v-for="user in newUsers">
            <span>编号:</span><span>{{user.id}}</span>
            <br>
            <span>姓名:</span><span>{{user.name}}</span>
          </div>
        </div>
        <div class="nouser" v-else>
          <h2>没有搜索到该姓名</h2>
        </div>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  name: 'search',
  data() {
    return {
      search: '', // 存放搜索文本框的内容
      users: [{
          id: 1,
          name: '张三'
        },
        {
          id: 2,
          name: '李四'
        },
        {
          id: 3,
          name: '乔峰'
        },
        {
          id: 4,
          name: '杨过'
        },
        {
          id: 5,
          name: '小龙女'
        },
        {
          id: 6,
          name: '黄蓉'
        },
        {
          id: 7,
          name: '刘备'
        },
        {
          id: 8,
          name: '张三丰'
        },
        {
        	id:9,
        	name:'刘邦'
        }
      ]
    }
  },
  computed: {
    newUsers() {
      return this.users.filter((item, index) => {
        return item.name.indexOf(this.search) != -1;
      });
    }
  }
}

</script>
<style scoped>
.box {
  /*padding: 5px;*/
  box-sizing: border-box;
  width: 800px;
  height: 600px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin: 10px auto;
}

.box .list {
  margin-top: 30px;
  display: flex;
  flex-flow: row wrap;
  /*换行*/
}

.box .list .item {
  width: 100px;
  height: 40px;
  border-radius: 4px;
  padding: 15px;
  margin: 10px;
  border: 1px solid #ccc;
}

.box .list .item:hover {
  border-color: #409EFF;
}

.box .nouser {
  color: #888;
  margin-top: 80px;
  font-size: 40px;
  text-align: center;
}

</style>
