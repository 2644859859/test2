<template>
  <d2-container :filename="filename">
    <template slot="header">新增数据</template>
    <d2-crud
      :columns="columns"
      :data="data"
      title="D2 CRUD"
      add-mode
      :add-button="addButton"
      :form-template="formTemplate"
      :form-options="formOptions"
      @row-add="handleRowAdd"
      @dialog-cancel="handleDialogCancel">
    </d2-crud>
    <el-card shadow="never" class="d2-mb">
      <d2-markdown :source="doc"/>
    </el-card>
    <el-card shadow="never" class="d2-mb">
      <d2-highlight :code="code"/>
    </el-card>
    <template slot="footer">
      <d2-link-btn title="文档" link="https://doc.d2admin.fairyever.com/zh/ecosystem-d2-crud/"/>
    </template>
  </d2-container>
</template>

<script>
import doc from './doc.md'
import code from './code.js'

export default {
  data () {
    return {
      filename: __filename,
      doc,
      code,
      columns: [
        {
          title: '日期',
          key: 'date'
        },
        {
          title: '姓名',
          key: 'name'
        },
        {
          title: '地址',
          key: 'address'
        }
      ],
      data: [
        {
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        },
        {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄'
        },
        {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        },
        {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }
      ],
      addButton: {
        icon: 'el-icon-plus',
        size: 'small'
      },
      formTemplate: {
        date: {
          title: '日期3',
          value: '2016-05-05'
        },
        name: {
          title: '姓名2',
          value: '王小虎'
        },
        address: {
          title: '地址1',
          value: '上海市普陀区金沙江路 1520 弄'
        }
      },
      formOptions: {
        labelWidth: '80px',
        labelPosition: 'left',
        saveLoading: false
      }
    }
  },
  methods: {
    handleRowAdd (row, done) {
      this.formOptions.saveLoading = true
      setTimeout(() => {
        console.log(row)
        this.$message({
          message: '保存成功',
          type: 'success'
        })
        done({
          address: '我是通过done事件传入的数据！'
        })
        this.formOptions.saveLoading = false
      }, 300)
    },
    handleDialogCancel (done) {
      this.$message({
        message: '取消保存',
        type: 'warning'
      })
      done()
    }
  }
}
</script>
