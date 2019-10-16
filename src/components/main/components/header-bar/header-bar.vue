<template>
  <div class="header-bar">
    <Row>
      <Col :xs="1" > <sider-trigger :collapsed="collapsed" icon="md-menu" @on-change="handleCollpasedChange"></sider-trigger></Col>
      <Col  :xs="0" :sm="0" :md="12" :lg="11"><custom-bread-crumb show-icon style="margin-left: 30px;" :list="breadCrumbList"></custom-bread-crumb></Col>
      <Col :xs="21" :sm="21" :md="11" :lg="11">  <div class="custom-content-con">
        <slot></slot>
      </div></Col>
    </Row>

  </div>
</template>
<script>
import siderTrigger from './sider-trigger'
import customBreadCrumb from './custom-bread-crumb'
import './header-bar.less'
export default {
  name: 'HeaderBar',
  components: {
    siderTrigger,
    customBreadCrumb
  },
  props: {
    collapsed: Boolean
  },
  computed: {
    breadCrumbList () {
      return this.$store.state.app.breadCrumbList
    }
  },
  methods: {
    handleCollpasedChange (state) {
      this.$emit('on-coll-change', state)
    }
  }
}
</script>
