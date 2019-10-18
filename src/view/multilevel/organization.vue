<template>
  <div class="otree">
    <Row class="secondtitle">
      <Col :xs="{span:23,push:1}" :sm="{span:17,push:1}">
        <h3>
          Organization Units
          <i>|</i>
          <span>应用组织机构和行政区划到用户和实体</span>
        </h3>
      </Col>
    </Row>
    <Row class="otreeContent mt-20">
      <!-- 左侧组织结构图 -->
      <Col :xs="24" :sm="{span:12}">
        <div class="treeleft">
          <div class="treehead">
            <Row>
              <Col :xs="24">组织结构树</Col>
              <Col :xs="24" >
                <Button type="primary" size="small" icon="md-add">添加根组织</Button>
                <Button type="primary" size="small" icon="md-add">添加子组织</Button>
                <Button type="primary" size="small" icon="md-create">修改</Button>
                <Button type="primary" size="small" icon="md-trash">删除</Button>
              </Col>
            </Row>
          </div>
          <Tree :data="otreedata" @on-select-change="selectItem"></Tree>
        </div>
      </Col>
      <!-- 右侧组织成员 -->
      <Col :xs="24" :sm="{span:12}">
        <div class="treeright">
          <div class="treehead">Quality Management</div>

        </div>
      </Col>
    </Row>
  </div>
</template>
<script>
export default {
  name: 'organization_page',
  data () {
    return {
      otreedata: [
        {
          title: 'parent 1',
          expand: true,
          children: [
            {
              title: 'parent 1-1',
              expand: true,
              children: [
                {
                  title: 'leaf 1-1-1'
                },
                {
                  title: 'leaf 1-1-2'
                }
              ]
            },
            {
              title: 'parent 1-2',
              expand: true,
              children: [
                {
                  title: 'leaf 1-2-1'
                },
                {
                  title: 'leaf 1-2-1'
                }
              ]
            }
          ]
        }
      ]
    }
  },
  methods: {
    selectItem (selectedArr, selectedItem) {
      console.log(selectedArr, selectedItem, 3333)
    }
  }
}
</script>
<style lang="less">
@import url("./user.less");
// 组织架构
.otree .ivu-tree ul {
  font-size: @fontsize;
}
.headborder{
    border-bottom: 1px solid #f2f2f2;
}
.treeleft,
.treeright {
  .backgroundfont;
  padding: 10px;
  margin: 10px;
}
.treehead {
  font-size: @fontsize;
.headborder;
  line-height: 30px;
  padding-bottom: 5px;
  overflow: hidden;
  .ivu-btn{
     margin: 3px 3px 0 3px ;
  }
}
</style>
