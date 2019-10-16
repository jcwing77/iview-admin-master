<template>
  <div class="roles">

       <Row  class="rolestitle">
        <Col :xs="{span:23,push:1}" :sm="{span:17,push:1}" :md="{span:17,push:1}" :lg="{span:17,push:1}">
           <h3>角色<i>|</i><span>使用角色进行权限分组.</span></h3></Col>
     <Col :xs="{ span: 22, offset: 1 }" :sm="{ span: 4, offset: 1 }" :md="{ span: 4, offset: 1}" :lg="{ span: 4, offset: 1 }">
     <div ><Button type="primary" icon="ios-search">添加角色</Button></div>
     </Col>

    </Row>

  </div>
</template>
<script>
export default {
  name: 'roles'
}
</script>
<style lang="less">
@fontsize:16px;
@color:#fff;
.roles{
   margin: -20px -20px 0 -20px;;

}
.backgroundfont{
 background: @color;
  border: 1px solid #dcdee2;
   border-radius: 5px;
}
.rolestitle{
   .backgroundfont;
    //  height: 40px;
    overflow: hidden;
     line-height: 40px;
  h3{

    font-size: @fontsize;
    padding-left: 1rem;
     font-weight: normal;
     i{
        padding: 0 10px;
        color: #e7e8ef;
     }
     span{
       color: #959cb6;
       font-size: 12px;
     }
  }
}

</style>
