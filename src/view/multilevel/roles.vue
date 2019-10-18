<template>
  <div class="roles">
    <Row class="secondtitle">
      <Col :xs="{span:23,push:1}" :sm="{span:17,push:1}">
        <h3>
          角色
          <i>|</i>
          <span>使用角色进行权限分组.</span>
        </h3>
      </Col>
      <Col :xs="{ span: 22}" :sm="{ span: 6}" class="addbtn">

          <Button type="primary" icon="md-add">添加角色</Button>

      </Col>
    </Row>
    <Row class="rolesContent">
          <Col :xs="24" :sm="{span:8}" >
        <Button type="primary" @click="permissions =true " long>Select Permissions (0)</Button>
      </Col>
      <Col :xs="24" :sm="16" class="refreshbtn">
        <Button  icon="md-refresh" type="primary"  :loading="loading1" @click="refreshData"> 刷新</Button>
      </Col>
      <Col :xs="24" class="rolesTable">
        <Table :loading="loading" :columns="columns12" :data="data6">
          <template slot-scope="{ row }" slot="name">
            <strong>{{ row.name }}</strong>
            <span v-if="row.tag1" class="tag">{{row.tag1}}</span>
            <span v-if="row.tag2" class="tag tag1">{{row.tag2}}</span>
          </template>
          <template slot-scope="{ row, index }" slot="action">
            <!-- <Button type="primary" size="small" style="margin-right: 5px" @click="show(index)">View</Button>
            <Button type="error" size="small" @click="remove(index)">Delete</Button>-->
            <Dropdown trigger="click" style="margin-left: 20px">
              <a href="javascript:void(0)">
                <Button icon="md-flower" type="primary">
                  操作
                  <Icon type="ios-arrow-down"></Icon>
                </Button>
              </a>
              <DropdownMenu slot="list">
                <DropdownItem>
                  <a href="javascript:0;" @click="show(index)">修改</a>
                </DropdownItem>
                <DropdownItem>
                  <a href="javascript:0;" @click="show(index)">删除</a>
                </DropdownItem>
              </DropdownMenu>
            </Dropdown>
          </template>
        </Table>
      </Col>
    </Row>

    <!-- 选择角色权限弹窗 -->
    <Modal
      v-model="permissions"
      title="Common Modal dialog box title"
      @on-ok="ok"
      @on-cancel="cancel"
    >
      <p>Content of dialog</p>
      <p>Content of dialog</p>
      <p>Content of dialog</p>
    </Modal>
  </div>
</template>
<script>
export default {
  name: 'roles',
  data () {
    return {
      permissions: false,
      loading1: false,
      loading: false,
      columns12: [
        {
          title: '角色名称',
          slot: 'name'
        },
        {
          title: '创建时间',
          key: 'time',
          sortable: true
        },

        {
          title: '操作',
          slot: 'action',
          width: 150,
          align: 'center'
        }
      ],
      data6: [
        {
          name: 'Admin',
          tag1: '系统',
          time: '2019-12-11'
        },
        {
          name: 'User',
          tag1: '系统',
          tag2: '默认',
          time: '2019-12-9'
        }
      ]
    }
  },
  methods: {
    refreshData () {
      // 刷新按钮
      let that = this

      this.loading1 = true

      setTimeout(function () {
        that.loading1 = false
      }, 1500)
    },
    ok () {
      this.$Message.info('Clicked ok')
    },
    cancel () {
      this.$Message.info('Clicked cancel')
    },
    show (index) {
      this.$Modal.info({
        title: 'User Info',
        content: `Name：${this.data6[index].name}<br>Age：${this.data6[index].age}<br>Address：${this.data6[index].address}`
      })
    },
    remove (index) {
      this.data6.splice(index, 1)
    }
  },
  created () {}
}
</script>
<style lang="less">
@import url("./user.less");
</style>
