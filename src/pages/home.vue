<template>
  <f7-page :page-content="false">
    <f7-navbar>
      <f7-nav-title>出差管理</f7-nav-title>
    </f7-navbar>
    <f7-toolbar tabbar labels :bottom-md="false">
      <f7-link tab-link="#tab1" tab-link-active text="出差申请" icon-ios="f7:person" icon-md="material:person"></f7-link>
      <f7-link tab-link="#tab2" text="申请一览" icon-ios="f7:today_fill" icon-md="material:today"></f7-link>
    </f7-toolbar>
    <f7-tabs>
      <f7-tab id="tab1" tab-active class="page-content">
        <f7-block-title>填写申请表</f7-block-title>
        <f7-list form>
          <f7-list-item>
            <f7-label>姓名</f7-label>
            <f7-input type="text" placeholder="请输入姓名" @change="handleValueChange($event, 'name')"></f7-input>
          </f7-list-item>
          <f7-list-item>
            <f7-label>工号</f7-label>
            <f7-input type="text" placeholder="请输入工号" @change="handleValueChange($event, 'id')"></f7-input>
          </f7-list-item>
          <f7-list-item>
            <f7-label>出差时间</f7-label>
            <div class="item-input-wrap">
              <input @click="openCalender" type="text" :value="form.dateRange" placeholder="请选择出差时间" readonly="readonly"/>
            </div>
          </f7-list-item>
          <f7-list-item>
            <f7-label>预算</f7-label>
            <div class="item-input-wrap">
              <f7-input type="number" placeholder="请输入预算" @change="handleValueChange($event, 'budget')"></f7-input>
            </div>
          </f7-list-item>
          <f7-segmented tag="p">
            <f7-button @click="handleCommit">提交</f7-button>
          </f7-segmented>
        </f7-list>
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
import Framework7 from 'framework7/framework7.esm.bundle.js';
import dayjs from 'dayjs';
export default {
  data: function () {
    return {
      form: {
        name: '',
        id: '',
        budget: null,
        dateRange: []
      },
      calendar: this.$f7.calendar.create({
        inputEl: '#calendar',
        openIn: 'customModal',
        toolbarCloseText: '确认',
        rangePicker: true,
        minDate: new Date(),
        footer: true,
        monthNames: ['一月', '二月', '三月', '四月', '五月', '六月', '七月', '八月', '九月', '十月', '十一月', '十二月'],
        monthNamesShort: ['一', '二', '三', '四', '五', '六', '七', '八', '九', '十', '十一', '十二'],
        dayNames: ['周日', '周一', '周二', '周三', '周四', '周五', '周六',],
        dayNamesShort: ['日', '一', '二', '三', '四', '五', '六',]
      }),
    };
  },
  created () {
    this.calendar.on('change', (_, val) => this.form.dateRange = val.map(d => dayjs(d).format('YYYY-MM-DD')));
  },
  methods: {
    openCalender () {
      this.calendar.open();
    },
    handleValueChange (e, key) {
      this.form[key] = e.target.value
    },
    handleCommit () {
      this.$f7.dialog.confirm('确定提交吗？', () => {
        console.log(this.form)
        this.$f7.dialog.alert('提交成功！');
      });
    }
  }
}
</script>
