<template>
  <div class="roles">
    <Row class="secondtitle">
      <Col :xs="{span:23,push:1}" :sm="{span:17,push:1}">
        <h3>
          用户
          <i>|</i>
          <span>管理用户及权限.</span>
        </h3>
      </Col>
      <Col :xs="{ span: 22}" :sm="{ span: 6}" class="addbtn">
        <Button type="primary" icon="md-add">添加用户</Button>
      </Col>
    </Row>
    <Row class="rolesContent">
      <!-- 搜索条 -->
      <Col :xs="24">
        <Input size="large" search enter-button placeholder="Enter something..." />
      </Col>
      <!-- 高级搜索条件 -->
      <Form :model="highFilter" class="highFilter" v-show="highFiltershow">
        <Col :xs="{span:12}">
          <Button type="primary" @click="permissions =true " long>Select Permissions (0)</Button>
        </Col>
        <Col :xs="{span:11,offset:1}">
          <FormItem>
            <Select v-model="model1" placeholder="按角色搜索">
              <Option
                v-for="item in cityList"
                :value="item.value"
                :key="item.value"
              >{{ item.label }}</Option>
            </Select>
          </FormItem>
        </Col>
        <Col :xs="12">
          <Checkbox v-model="highFilter.single">仅已锁定用户</Checkbox>
        </Col>
        <Col :xs="12" class="refreshbtn">
          <Button icon="md-refresh" type="primary" :loading="loading1" @click="refreshData">刷新</Button>
        </Col>
      </Form>
      <Col :xs="24">
        <Button style="margin-top:20px" @click="showHighFilter">
          <Icon type="ios-arrow-up" v-show="highFiltershow" />
          <Icon type="ios-arrow-down" v-show="!highFiltershow" />
          {{highFiltershow?'隐藏高级过滤':'显示高级过滤'}}
        </Button>
      </Col>
      <Col :xs="24" class="rolesTable">
        <!-- 表格数据 -->
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
      <Col :xs="24">
        <div class="mt-20">
          <Page
            :total="100"
            show-sizer
            show-elevator
            show-total
            @on-change="page"
            @on-page-size-change="pageSize"
          />
        </div>
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
  name: 'users',
  data () {
    return {
      permissions: false,
      loading1: false,
      loading: false,
      highFiltershow: false,
      highFilter: {
        single: false
      },
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
      ],
      // 下拉菜单
      cityList: [
        {
          value: 'New York',
          label: 'New York'
        },
        {
          value: 'London',
          label: 'London'
        },
        {
          value: 'Sydney',
          label: 'Sydney'
        },
        {
          value: 'Ottawa',
          label: 'Ottawa'
        },
        {
          value: 'Paris',
          label: 'Paris'
        },
        {
          value: 'Canberra',
          label: 'Canberra'
        }
      ],
      model1: ''
    }
  },
  methods: {
    page (pno) {
      // 获取当前点击页码
      console.log(pno)
    },
    pageSize (pageSize) {
      // 获取分页条数
      console.log(pageSize)
    },
    showHighFilter () {
      if (this.highFiltershow === true) {
        this.highFiltershow = false
      } else {
        this.highFiltershow = true
      }
    },
    refreshData () {
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
