<template>
  <div>
    <footer class="footer">
      <div class="clearfix"></div>
      <div class="icon-row">
        <div class="footer-icon">
          <h5 class="footer-icon-child"></h5>
          <span class="footer-icon-text">品质保障</span>
        </div>
        <div class="footer-icon">
          <h5 class="footer-icon-child footer-icon-child-2"></h5>
          <span class="footer-icon-text">七天无理由退换货</span>
        </div>
        <div class="footer-icon">
          <h5 class="footer-icon-child footer-icon-child-3"></h5>
          <span class="footer-icon-text">特色服务体现</span>
        </div>
        <div class="footer-icon">
          <h5 class="footer-icon-child footer-icon-child-4"></h5>
          <span class="footer-icon-text">帮助中心</span>
        </div>
      </div>
      <div class="service-intro">
        <div class="servece-type">
          <div class="servece-type-info" v-for="(guide, index) in guideArr" :key="index">
            <ul>
              <li v-for="(item, index) in guide" :key="index">
                <span>{{item}}</span>
              </li>
            </ul>
          </div>
        </div>
        <div class="clearfix"></div>
        <div class="friend-link">
          <div class="friend-link-item">
            <ul>
              <li v-for="(link, index) in moreLink" :key="index">
                <span :class="[linkItemClass, {'link-last-item': index === 9}]">{{link}}</span>
              </li>
            </ul>
          </div>
        </div>
        <div class="clearfix"></div>
        <div class="copyright">
          <p>Copyright © 2019 by 版权所有:榴莲购</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Footer',
  data () {
    return {
      linkItemClass: 'link-item',
      guideArr: [
        ['购物指南', '免费注册', '开通支付宝', '支付宝充值'],
        [ '榴莲购保障', '发票保障', '售后规则', '缺货赔付' ],
        [ '支付方式', '快捷支付', '信用卡', '余额宝', '蚂蚁花呗', '货到付款' ],
        ['平台直播课堂', '店铺直播', '新手直播', '折扣直播'],
        ['平台直播课堂', '榴莲规则', '商家入驻', '商家中心', '榴莲智库', '物流服务', '商家中心']
      ],
      moreLink: [
        '关于榴莲', '帮助中心', '开发平台', '诚聘英才', '联系我们', '网站合作', '法律声明', '隐私权政策', '廉政举报', '规则意见征集'
      ]
    };
  }
};
</script>

<style scoped>
/*****************************底 部 开 始*****************************/
.footer {
  width: 100%;
  height: 390px;
  margin-top: 30px;
  background-color: #eaeaea;
}
.icon-row {
  margin: 15px auto;
  padding-top: 8px;
  width: 1000px;
  height: 64px;
}
.footer-icon {
  margin-left: 87px;
  margin-right: 17px;
  float: left;
}
.footer-icon-child {
  margin-top: 10px;
  overflow: hidden;
  position: absolute;
  width: 36px;
  height: 42px;
  background-image: url("../../../static/img/footer/ico_service.png");
  text-indent: -999px;
}
.footer-icon-child-2 {
  background-position: 0 -43px;
}
.footer-icon-child-3 {
  background-position: 0 -86px;
}
.footer-icon-child-4 {
  background-position: 0 -129px;
}
.footer-icon-text {
  margin-left: 45px;
  color: #444444;
  font-size: 18px;
  font-weight: bold;
  line-height: 64px;
}
.service-intro {
  width: 100%;
  border-top: 1px solid #b2dfdb;
}
.servece-type {
  margin: 15px auto;
  height: 200px;
  width: 800px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.servece-type-info {
  color: #666666;
}
.servece-type-info ul {
  list-style: none;
}
.servece-type-info li {
  font-size: 14px;
  cursor: pointer;
  line-height: 26px;
}
.servece-type-info li:first-child {
  font-size: 16px;
  line-height: 28px;
  font-weight: bold;
}
.friend-link {
  display: flex;
  align-items: center;
  width: 908px;
  height: 30px;
  margin: 0px auto;
  color: #666;
  border-top: 1px solid #b2dfdb;
}
.friend-link-item {
  margin: 0px auto;
}
.friend-link-item ul {
  list-style: none;
}
.friend-link-item li {
  padding: 5px 0px;
  float: left;
}
.link-item {
  padding: 0px 8px;
  cursor: pointer;
  border-right: 1px solid #ccc;
}
.link-last-item {
  border: none;
}
.copyright {
  width: 100%;
  color: #666;
  line-height: 30px;
  text-align: center;
}
.copyright a{
  color: #232323;
  font-size: 20px;
}
/*****************************底 部 结 束*****************************/
</style>
