<template>
  <f7-page :page-content="false">
    <f7-navbar>
      <f7-nav-title>出差管理</f7-nav-title>
    </f7-navbar>
    <f7-toolbar tabbar labels :bottom-md="isBottom">
      <f7-link tab-link="#tab1" tab-link-active text="Tab 1" icon-ios="f7:email_fill" icon-md="material:email"></f7-link>
      <f7-link tab-link="#tab2" text="Tab 2" icon-ios="f7:today_fill" icon-md="material:today"></f7-link>
    </f7-toolbar>
    <f7-tabs>
      <f7-tab id="tab1" tab-active class="page-content">
        <f7-block>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nisi nisi, tincidunt ut eleifend non, sagittis a elit. Sed consequat odio at leo varius viverra...</p>
        </f7-block>
      </f7-tab>
      <f7-tab id="tab2" class="page-content">
        <f7-block>
          <p>Donec iaculis posuere massa sed dignissim. Praesent id nibh nec massa mollis egestas. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas...</p>
        </f7-block>
      </f7-tab>
    </f7-tabs>
  </f7-page>
</template>
<script>
export default {}
</script>
