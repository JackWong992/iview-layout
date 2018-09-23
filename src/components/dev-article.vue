<template>
  <Layout>
    <Header class="header">
      <Row>
        <i-col span="4" offset="1">
          <img src="https://file.iviewui.com/dist/e1cf12c07bf6458992569e67927d767e.png" alt="logo" width="128">
        </i-col>
        <i-col span="14">
        <Menu mode="horizontal"  :active-name="activeName">
            <MenuItem name="/app" to="/app">应用分享</MenuItem>
            <MenuItem name="/push" to="/push">推送营销</MenuItem>
            <MenuItem name="/dev" to="/dev">开发助手</MenuItem>
            <MenuItem name="/manage" to="/manage">应用管理</MenuItem>
        </Menu>
        </i-col>
        <i-col span="4">
            <Row>
              <i-col span="8">
                <Dropdown>
                  <Avatar src="https://avatars2.githubusercontent.com/u/32337128?s=460&v=4"></Avatar>
                  <DropdownMenu slot="list">
                    <DropdownItem>我的主页</DropdownItem>
                    <DropdownItem>我的收藏</DropdownItem>
                    <DropdownItem>设置
                      <Badge status="error" />
                    </DropdownItem>
                    <DropdownItem divided>退出</DropdownItem>
                  </DropdownMenu>
                </Dropdown>
              </i-col>
              <i-col span="8">
                <Dropdown>
                  <Badge :count="2" :offset="[20,4]">
                    <Icon type="md-notifications" size="24" />
                  </Badge>
                  <DropdownMenu slot="list">
                    <Tabs value="name1">
                      <TabPane label="通知" name="notification">
                        <div class="notifucation">通知内容</div>
                      </TabPane>
                      <TabPane label="关注" name="follow">
                        <div class="notifucation">关注内容</div>
                      </TabPane>
                      <TabPane label="系统" name="system">
                        <div class="notifucation">系统内容</div>
                      </TabPane>
                    </Tabs>
                  </DropdownMenu>
                </Dropdown>
              </i-col>
              <i-col span="8">
                <Icon type="md-color-palette"  size="24" @click="handleClickOpenTheme" />
              </i-col>
            </Row>
        </i-col>
      </Row>
    </Header>
    <Layout>
      <Sider class="sider" width="240" collapsible v-model="isCollapsible" :class="{'sider-hide': isCollapsible }">
        <Menu class="sider-menu" theme="dark" active-name="option2">
          <MenuItem name="option1">
            <Icon type="ios-search" />
            <span>Option1</span>
          </MenuItem>
          <MenuItem name="option2">
            <Icon type="ios-apps" />
            <span>Option2</span>
          </MenuItem>
          <MenuItem name="option3">
            <Icon type="ios-bookmark" />
            <span>Option3</span>
          </MenuItem>
        </Menu>
      </Sider>
      <Content class="content" :class="{'content-expand': isCollapsible }">
        <Breadcrumb>
          <BreadcrumbItem to="/">
            Home
          </BreadcrumbItem>
          <BreadcrumbItem to="/app">
            app
          </BreadcrumbItem>

          <BreadcrumbItem to="/push">
            push
          </BreadcrumbItem>

        </Breadcrumb>
        <Card style="margin-top: 16px" class="breadCard">
          <slot></slot>
        </Card>
      </Content>
    </Layout>
    <Drawer title="选择配色" v-model="openTheme"></Drawer>
  </Layout>
</template>

<script>
export default {
  data() {
    return {
      activeName: this.$route.path,
      openTheme: false,
      isCollapsible: false
    }
  },
  methods: {
    handleClickOpenTheme(){
      this.openTheme = true
    }
  },
  created(){
    this.activeName = this.$route.path
  }
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 2;
  background: #fff;
  width: 100%;
  height: 60px;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
 .notifucation{
   text-align: center;
   height: 200px;
 }
  .ivu-menu-horizontal.ivu-menu-light:after {
    display: none;
  }
  .sider {
    position: fixed;
    height: 100%;
    left: 0;
    overflow: hidden;
    z-index: 1;
  }
  .sider-menu {
    margin-top: 60px;
  }
  .sider-hide .ivu-menu-item span {
    display: none;
  }
  .content {
    margin-left: 240px;
    margin-top: 60px;
    padding: 16px;
    transition: all .2s ease-in-out;
  }
  .content-expand{
    margin-left: 64px;
  }
  .breadCard{
    height: 600px;
  }
</style>
