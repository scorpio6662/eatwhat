<template>
  <div>
    <div>
      <el-table
          :data="tableData"
          :header-cell-style="{background:'#F2F6FC', padding: '6px 0px', color: '#606266'}"
          style="width: 100%"
          border>
        <el-table-column prop="num" label="序号" width="50">
        </el-table-column>
        <el-table-column prop="name" label="餐厅名称" width="120">
        </el-table-column>
        <el-table-column prop="type" label="类型" width="120">
        </el-table-column>
        <el-table-column prop="must_eat" label="必吃菜" width="120">
        </el-table-column>
        <el-table-column prop="address" label="地址" width="300">
        </el-table-column>
        <el-table-column prop="like" label="喜好程度" width="120">
        </el-table-column>
        <el-table-column prop="done" label="是否已吃" width="120">
        </el-table-column>
        <el-table-column  label="操作" width="100">
          <template slot-scope="scope">
            <el-button  type="text" size="small" @click="update(scope.row)">编辑</el-button>
            <el-button type="text" size="small" @click="delete(scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
    <el-dialog title="更新列表":visible.sync="dialogFormVisible" append-to-body>
      <el-form :model="listForm" ref="form" label-width="80px">
        <el-form-item label="餐厅名称" prop="name">
            <el-input v-model.name="listForm.name"></el-input>
          </el-form-item>
        <el-form-item label="类型" prop="type">
          <el-input v-model.name="listForm.type"></el-input>
        </el-form-item>
      </el-form>

      <div slot="footer" class="dialog-footer">
        <el-form-item>
          <el-button @click="dialogFormVisible = false">取消</el-button>
          <el-button type="primary" @click="update">确定</el-button>
        </el-form-item>
      </div>
    </el-dialog>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick(row) {
      console.log(row);
    },
    update(row){
        this.dialogFormVisible = true;
        this.listForm.name = '111'
        this.listForm.type = '222'
    },
    delete(row){
      debugger;
      console.log(row);
    }
  },

  data() {
    return {
      dialogFormVisible: false,
      tableData: [{
        num: '1',
        name: '海底捞',
        type: '火锅',
        city: '普陀区',
        address: 'xxxx',
        must_eat:'牛肉',
        like:'三星',
        done:'N'

      }, {
        num: '2',
        name: '包装马车',
        type: '韩餐',
        city: '普陀区',
        address: '望京',
        must_eat:'牛肉',
        like:'三星',
        done:'N'
      }, {
        num: '3',
        name: '马路边边',
        type: '串串',
        city: '普陀区',
        address: '北清路68号',
        must_eat:'牛肉',
        like:'三星',
        done:'N'
      }],
      listForm:{
        name:''
      }
    }
  }
}
</script>
