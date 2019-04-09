<template>
  <div>
    <div class="item-intro-show">
      <!--<div class="item-intro-recommend">
        <div class="item-recommend-title">
          <p>店铺热销</p>
        </div>
        <div class="item-intro-recommend-column">
          <div class="item-recommend-column" v-for="(item, index) in goodsInfo.hot" :key="index">
            <div class="item-recommend-img">
              <img :src="item.img" alt="">
            </div>
            <div class="item-recommend-intro">
              <span>
                <span class="item-recommend-top-num">{{index + 1}}</span> 热销{{item.sale}}件</span>
              <span class="item-recommend-price">￥{{item.price.toFixed(2)}}</span>
            </div>
          </div>
        </div>
      </div>-->
      <div class="item-intro-detail" ref="itemIntroDetail">
        <div class="item-intro-nav item-tabs">
          <Tabs>
            <TabPane label="搭配神器">
              <div class="remarks-title">
                <span>搭配神器</span>
              </div>
              <div class="item-intro-img" ref="itemIntroGoods">
                <img :src="item" alt="" v-for="(item,index) in goodsInfo.goodsDetail" :key="index">
                <div class="item-intro-price">
                	<p>套餐价：<span>￥608.00</span></p>
                	<p>查看套餐</p>
                </div>
              </div>
            </TabPane>
            <TabPane label="秋装优惠券">
              <div class="remarks-title">
                <span>秋装优惠券</span>
              </div>
              <div class="item-param-container">
                <span class="item-param-box" v-for="(item,index) in goodsInfo.param" :key="index">
                  <span class="item-param-title">{{item.title}}: </span>
                  <span class="item-param-content">{{item.content}}</span>
                </span>
              </div>
            </TabPane>
            <!--<TabPane label="售后保障">
              <ShowProductWarranty></ShowProductWarranty>
            </TabPane>-->
            <TabPane label="搭配">
              <div class="remarks-container">
                <div class="remarks-title">
                  <span>搭配</span>
                </div>
                <div class="remarks-analyse-box">
                  <div class="remarks-analyse-goods">
                    <i-circle :percent="goodsInfo.remarks.goodAnalyse" stroke-color="#e4393c">
                      <span class="remarks-analyse-num">{{goodsInfo.remarks.goodAnalyse}}%</span>
                      <p class="remarks-analyse-title">好评率</p>
                    </i-circle>
                  </div>
                  <div class="remarks-analyse-tags">
                    <Tag checkable :color="tagsColor[index % 4]" v-for="(item,index) in goodsInfo.remarks.remarksTags" :key="index">{{item}}</Tag>
                  </div>
                </div>
                <div class="remarks-bar">
                  <span>追评({{goodsInfo.remarks.remarksNumDetail[0]}})</span>
                  <span>好评({{goodsInfo.remarks.remarksNumDetail[1]}})</span>
                  <span>中评({{goodsInfo.remarks.remarksNumDetail[2]}})</span>
                  <span>差评({{goodsInfo.remarks.remarksNumDetail[3]}})</span>
                </div>
                <div class="remarks-box" v-for="(item,index) in goodsInfo.remarks.detail" :key="index">
                  <div class="remarks-user">
                    <Avatar icon="person" />
                    <span class="remarks-user-name">{{item.username}}</span>
                  </div>
                  <div class="remarks-content-box">
                    <p>
                      <Rate disabled :value="item.values" allow-half class="remarks-star"></Rate>
                    </p>
                    <p class="remarks-content">{{item.content}}</p>
                    <p class="remarks-sub">
                      <span class="remarks-item">{{item.goods}}</span>
                      <span class="remarks-time">{{item.time}}</span>
                    </p>
                  </div>
                </div>
                <div class="remarks-page">
                  <Page :total="40" size="small" show-elevator show-sizer></Page>
                </div>
              </div>
            </TabPane>
          </Tabs>
        </div>
      </div>
    </div>
    <!--商家详情-->
    <div class="shop-detail">
    	<div class="shop-detail-left">
    		<div class="shop-detail-top">
    			<p class="shop-tang">唐狮官方旗舰店</p>
    			<ul class="shop-tang-describe">
    				<li>
    					<span>描述</span><br /><span class="describe-point">4.7</span>
    				</li>
    				<li>
    					<span>服务</span><br /><span class="describe-point">4.8</span>
    				</li>
    				<li>
    					<span>物流</span><br /><span class="describe-point">4.7</span>
    				</li>
    			</ul>
    			<div class="shop-come">
    				<p class="shop-come-one">进店逛逛</p>
    				<p class="shop-come-two">收藏店铺</p>
    			</div>
    		</div>
    		<div class="shop-detail-bot">
    			<p class="shop-tang">本店搜索</p>
    			<ul class="shop-search">
    				<li>
    					<span>关键字</span>&nbsp;&nbsp;<input type="text" class="shop-search-one" />
    				</li>
    				<li>
    					<span>价格</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="number" class="shop-search-two" /> - <input type="number" class="shop-search-two" />
    				</li>
    				<li>
    					<button class="shop-search-three">搜索</button>
    				</li>
    			</ul>
    		</div>
    	</div>
    	<div class="shop-detail-mid">
    		<p class="detail-mid-title">
    			<span class="font-color">商品详情</span> &nbsp;&nbsp;&nbsp;<span>累计评价</span><span class="font-color-one">16644</span><span class="shop-phone">手机购买</span>
    		</p>
    		<p class="detail-mid-plan">
    			该商品参与了公益宝贝计划，卖家承诺每笔成交将为<span class="font-color">顶梁柱重病救助行动</span>捐赠<span class="font-color">0.02元</span> 该商品已经累计捐赠<span class="font-color">52802笔</span>
    		</p>
    		<div class="detail-mid-cont">
    			<p class="detail-pai">品牌名称：tonlion/唐狮</p>
    			<p class="detail-can">产品参数：</p>
    			<ul class="detail-can-cont">
    				<li>
    					<p><span>品牌：</span><span>tonlion/唐狮</span></p>
    					<p><span>图案：</span><span>纯色</span></p>
    					<p><span>衣们襟：</span><span>单排扣</span></p>
    					<p><span>货号：</span><span>T616321052434</span></p>
    					<p><span>厚薄：</span><span>常规</span></p>
    					<p><span>流行元素/工艺：</span><span>口袋 纽扣</span></p>
    				</li>
    				<li>
    					<p><span>使用年龄：</span><span>18-24周岁</span></p>
    					<p><span>风格：</span><span>百搭</span></p>
    					<p><span>颜色分类：</span><span>浅牛仔蓝</span></p>
    					<p><span>年份季节：</span><span>2019年秋季</span></p>
    					<p><span>衣长：</span><span>常规</span></p>
    					<p><span>销售渠道类型：</span><span>商城同款</span></p>
    				</li>
    				<li>
    					<p><span>尺寸：</span><span>S &nbsp;M &nbsp;L</span></p>
    					<p><span>领子：</span><span>POLO领</span></p>
    					<p><span>组合形式：</span><span>单件</span></p>
    					<p><span>袖长：</span><span>长袖</span></p>
    					<p><span>服装版型：</span><span>宽松</span></p>
    					<p><span>材质成分：</span><span>棉100%</span></p>
    				</li>
    			</ul>
    		</div>
    	</div>
    	<div class="shop-detail-right">
    		<ul class="detail-product">
    			<li>产品图</li>
    			<li>尺寸及试穿</li>
    			<li>模特及效果</li>
    			<li>效果图</li>
    			<li>服务质量</li>
    		</ul>
    	</div>
    </div>
  	<!--图片介绍  留出位置-->
  	<div></div>
  	<!--价格说明-->
  	<div class="price-shuo">
  		<p class="price-shuo-title">价格说明</p>
  		<ul class="price-shuo-cont">
  			<li>
  				<span class="dian"></span><p><span class="hua">划线价格：</span>指商品的专柜价、品牌价、正品零售价、厂家指导价或该商品曾经展示过得零售价，<span class="hua">并非原价,</span>仅供参考</p>
  			</li>
  			<li>
  				<span class="dian"></span><p><span class="hua">未划线价格：</span>指商品的<span class="hua">实际标价</span>，不因表述的差异改变性质，具体成交价格根据商品参加活动，
  				或会员使用优惠券、积分等发生变化，最终以订单结算页价格为准。
  				</p>
  			</li>
  			<li>
  				<span class="dian"></span><p>商家详情页(含主图)以图片或文字形式标准的一口价、促销价、优惠价等价格可能是使用优惠券、满减或特定优惠活动
  				和时段等情形下的价格，具体请以结算页面的标价、优惠价或活动规则为准。
  				</p>
  			</li>
  			<li>
  				<span class="dian"></span><p>此说明仅当出现价格比较时有效，具体请参见《淘宝价格发布规范》</p>
  			</li>
  		</ul>
  	</div>
  	<!--用户评论-->
  	<div class="user-com">
  		<p class="user-com-title">累计评价16644</p>
  		<div class="user-com-cont">
  			<div class="com-cont-one">
  				<p class="com-cont-fu">与描述相符</p>
  				<p class="com-cont-shu">4.8</p>
  			</div>
  			<div class="com-cont-line"></div>
  			<p class="com-cont-zi">大家都写到</p>
  			<div class="com-cont-two">
  				<ul class="com-cont-style">
  					<li>版型漂亮(303)</li>
  					<li>质量不错(290)</li>
  					<li>颜色很美(123)</li>
  					<li>穿着漂亮(115)</li>
  					<li>料子不错(278)</li>
  					<li>很舒适(278)</li>
  					<li style="border: 1px solid #C8C7C6; color: #96CA76;">不舒适(78)</li>
  				</ul>
  			</div>
  		</div>
  		<div class="user-com-bot">
  			<div class="user-com-all">
  				<p><input type="radio" name="all" id="all" checked="checked"/>全部</p>
  				<p><input type="radio" name="all" id="zhui" />追评(612)</p>
  				<p><input type="radio" name="all" id="pic" />图片(1625)</p>
  			</div>
  			<div class="user-com-right">
  				<p><input type="checkbox" name="" id="" value="" checked="checked"/>有内容</p>
  				<button>按默认</button>
  			</div>
  		</div>
  	</div>
  	<!--评论区-->
  	<div class="comment-all">
  		<ul class="comment-all-cont" v-for="(item,index) in goodsInfo.remarks.detail" :key="index">
  			<li class="comment-all-left">
  				<p class="user-comment"><!--牛仔衣不错，没有很难闻的牛仔衣的味道，还是很不错的，布料也不像那种硬邦邦的牛仔布，穿上很舒服，天气转暖了
  				所以我买的是相对浅色的牛仔衣，很好搭衣服，我感觉南方的朋友冬天可以穿，里面可以搭配一个浅色的卫衣，很好看的呀，切记：牛仔衣最好不要内搭深色
  				的衣服，这样显得古怪，没有搭配浅色衣服看着好看，我发现牛仔衣简直是万能搭配，下面搭配什么都可以，真的很棒呀。-->
  				{{item.content}}
  				</p>
  				<ul class="user-pics">
  					<li><img src="../../../static/img/goodsDetail/psd/直播/images/宝贝详情_18.gif"/></li>
  				</ul>
  				<p class="comment-date">{{item.create_at}}</p>
  				<p class="explain"></p>
  			</li>
  			<li class="comment-all-mid">
  				<p>{{item.goods}}</p>
  				<p>尺码:L</p>
  			</li>
  			<li class="comment-all-right">
  				<p>{{item.username}}</p>
  			</li>
  		</ul>
  		<div class="remarks-page">
	      <Page :total="40" size="small" show-elevator show-sizer></Page>
	    </div>
  	</div>
  </div>
</template>

<script>
import ShowProductWarranty from '@/components/goodsDetail/ShowProductWarranty';
import store from '@/vuex/store';
import { mapState } from 'vuex';
export default {
  name: 'ShowGoodsDetail',
  data () {
    return {
      tagsColor: [ 'blue', 'green', 'red', 'yellow' ]
    };
  },
  computed: {
    ...mapState(['goodsInfo'])
  },
  methods: {
    changeHeight () {
      let heightCss = window.getComputedStyle(this.$refs.itemIntroGoods).height;
      console.log(heightCss);
      heightCss = parseInt(heightCss.substr(0, heightCss.length - 2)) + 89;
      this.$refs.itemIntroDetail.style.height = heightCss + 'px';
    }
  },
  updated () {
    this.$nextTick(() => {
      setTimeout(this.changeHeight, 100);
      setTimeout(this.changeHeight, 1000);
      setTimeout(this.changeHeight, 3000);
      setTimeout(this.changeHeight, 5000);
      setTimeout(this.changeHeight, 10000);
      setTimeout(this.changeHeight, 15000);
      setTimeout(this.changeHeight, 20000);
      setTimeout(this.changeHeight, 25000);
      setTimeout(this.changeHeight, 30000);
      setTimeout(this.changeHeight, 50000);
    });
  },
  components: {
    ShowProductWarranty
  },
  store
};
</script>

<style scoped>
/***************商品详情介绍和推荐侧边栏开始***************/
/*评论区展示*/
.comment-all{
	width: 900px;
	margin: 0 auto;
}
.comment-all-cont{
	width: 900px;
	height: 300px;
	font-weight: bold;
	margin-top: 15px;
	border-bottom: 2px solid black;
	display: flex;
	justify-content: space-between;
}
.comment-all-left{
	width: 500px;
	height: 300px;
}
.comment-all-right,
.comment-all-mid{
	width: 150px;
	height: 40px;
	margin-top: 130px;
}
.user-pics{
	width: 500px;
	height: 60px;
	margin-top: 10px;
	overflow: hidden;
}
.user-pics li{
	width: 60px;
	height: 60px;
	float: left;
	margin-left: 10px;
}
.user-pics img{
	width: 100%;
}
.comment-date{
	width: 100%;
	margin-top: 10px;
}
.explain{
	width: 100%;
	color: #DCCAAF;
	margin-top: 10px;
}
/*用户评论*/
.user-com-cont{
	width: 900px;
	height: 150px;
	border: 1px solid gray;
}
.com-cont-one{
	width: 150px;
	height: 150px;
	text-align: center;
	float: left;
}
.com-cont-fu{
	width: 150px;
	margin-top: 20px;
	font-size: 20px;
}
.com-cont-shu{
	width: 150px;
	font-size: 50px;
	color: #ED6D20;
}
.com-cont-line{
	width: 1px;
	height: 100px;
	float: left;
	margin-top: 20px;
	background: gray;
}
.com-cont-zi{
	width: 5px;
	height: 100px;
	float: left;
	margin-top: 20px;
	margin-left: 10px;
	color: gray;
}
.com-cont-two{
	width: 700px;
	height: 150px;
	float: left;
	margin-left: 20px;
}
.com-cont-style{
	width: 500px;
	height: 100px;
	float: left;
	margin-top: 20px;
}
.com-cont-style li{
	width: 100px;
	height: 40px;
	border: 2px solid orange;
	text-align: center;
	line-height: 40px;
	color: #F08669;
	font-weight: bold;
	float: left;
	margin-left: 20px;
	margin-top: 5px;
	cursor: pointer;
}
.user-com-bot{
	width: 900px;
	height: 30px;
	line-height: 30px;
	border: 1px solid gray;
	border-top: 0px;
	display: flex;
	justify-content: space-between;
}
.user-com{
	width: 900px;
	margin: 0 auto;
}
.user-com-title{
	width: 900px;
	height: 30px;
	line-height: 30px;
	background: red;
	color: white;
	text-indent: 16px;
}
.user-com-all{
	width: 300px;
	display: flex;
	justify-content: space-around;
}
.user-com-right input,
.user-com-all input{
	float: left;
	margin-top: 9px;
	margin-right: 4px;
}
.user-com-right{
	width: 150px;
	display: flex;
	justify-content: center;
	
}

.user-com-right button{
	width: 60px;
	height: 20px;
	line-height: 15px;
	margin-top: 5px;
	margin-left: 10px;
}
/*价格说明*/
.price-shuo{
	width: 900px;
	margin: 20px auto;
}
.price-shuo-title{
	width: 900px;
	height: 30px;
	color: white;
	background: red;
	font-weight: bold;
	line-height: 30px;
	text-indent: 16px;
}
.price-shuo-cont li{
	height: 30px;
	margin-top: 10px;
}
.dian{
	display: block;
	float: left;
	width: 5px;
	height: 5px;
	border-radius: 50%;
	background: red;
	margin-left: 15px;
	margin-top: 5px;
}
.hua{
	color: black;
	font-weight:bold ;
}
.price-shuo-cont p{
	width: 850px;
	height: 30px;
	float: left;
	margin-left: 10px;
	color: gray;
}
/*商家详情*/

.shop-detail{
	width: 1200px;
	height: 400px;
	margin: 0 auto;
	display: flex;
	justify-content: space-between;
}
.shop-detail-left{
	width: 200px;
	height: 400px;
}
.shop-detail-top{
	width: 198px;
	height: 180px;
	border: 1px solid gray;
}
.shop-detail-bot{
	width: 100%;
	height: 180px;
	border: 1px solid gray;
	margin-top: 40px;
}
.shop-tang{
	width: 100%;
	height: 30px;
	text-align: center;
	line-height: 30px;
	font-size: 18px;
	font-weight: bold;
	border: 1px solid gray;
}
.shop-tang-describe{
	width: 160px;
	height: 40px;
	margin: 0 auto;
	margin-top: 40px;
	text-align: center;
	font-weight: bold;
	display: flex;
	justify-content: space-around;
}
.describe-point{
	color: #6B815A;
}
.shop-come{
	width: 196px;
	height: 30px;
	margin-top: 10px;
	display: flex;
	justify-content: space-around;
}
.shop-come-one{
	width: 80px;
	height: 30px;
	text-align: center;
	background: black;
	color: white;
	line-height: 30px;
}
.shop-come-two{
	width: 80px;
	height: 30px;
	text-align: center;
	border: 1px solid black;
	line-height: 30px;
}
.shop-search{
	width: 180px;
	height: 100px;
	font-weight: bold;
	margin: 0 auto;
}
.shop-search li{
	width: 100%;
	margin-top: 10px;
}
.shop-search-one{
	width: 120px;
	height: 20px;
}
.shop-search-two{
	width: 50px;
	height: 20px;
}
.shop-search-three{
	width: 100px;
	height: 20px;
	margin-left: 40px;
	background: orange;
	color: white;
	text-align: center;
	outline: none;
	border: 0px;
}
.shop-detail-mid{
	width: 700px;
	height: 400px;
	border: 1px solid gray;
}
.detail-mid-title{
	width: 700px;
	height: 40px;
	font-weight: bold;
	border: 1px solid gray;
	line-height: 40px;
}
.detail-mid-plan{
	width: 700px;
	height: 40px;
	font-weight: bold;
	text-align: center;
	line-height: 40px;
	border: 1px solid gray;
}
.detail-mid-cont{
	width: 700px;
	height: 320px;
	border: 1px solid gray;
}
.detail-pai{
	width: 650px;
	height: 50px;
	margin-top: 20px;
	margin-left: 10px;
	line-height: 50px;
}
.detail-can{
	width: 650px;
	height: 30px;
	margin-left: 10px;
	line-height: 30px;
}
.detail-can-cont{
	width: 680px;
	height: 200px;
	margin: 20px auto;
	display: flex;
	justify-content: space-between;
}
.detail-can-cont p{
	margin-top: 10px;
}
.font-color{
	color: orange;
}
.font-color-one{
	color: #515BA2;
	font-weight: bold;
}
.shop-phone{
	float: right;
	margin-right: 20px;
	cursor: pointer;
}
.shop-detail-right{
	width: 200px;
	height: 400px;
}
.detail-product{
	width: 150px;
	height: 300px;
	margin: 50px auto;
	font-weight: bold;
}
.detail-product li{
	margin-top: 20px;
}
.item-intro-show{
  width: 80%;
  margin: 15px auto;
  display: flex;
  flex-direction: row;
  background-color: #fff;
}
.item-intro-recommend{
  width: 200px;
  display: flex;
  flex-direction: column;
}
.item-intro-recommend-column{
  display: flex;
  flex-direction: column;
  box-shadow: 0px 0px 5px #999;
}
.item-recommend-title{
  width: 100%;
  height: 38px;
  font-size: 16px;
  line-height: 38px;
  color: #fff;
  background-color: #E4393C;
  box-shadow: 0px 0px 5px #E4393C;
  text-align: center;
}
.item-recommend-column{
  margin-top: 15px;
}
.item-recommend-intro{
  padding: 5px 15px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  font-size: 12px;
  color: #999;
  cursor: pointer;
}
.item-recommend-img{
  width: 80%;
  margin: 0px auto;
  cursor: pointer;
}
.item-recommend-img img{
  width: 100%;
}
.item-recommend-top-num{
  color: #fff;
  margin: 0px 2px;
  padding: 1px 5px;
  border-radius: 12px;
  background-color: #E4393C;
}
.item-recommend-price{
  color: #E4393C;
  font-weight: bolder;
}
.item-intro-detail{
  width: 1200px;
}
.item-intro-nav{
  width: 100%;
  height: 38px;
  background-color: #F7F7F7;
  border-bottom: 1px solid #E4393C;
}
.item-intro-nav ul{
  margin: 0px;
  padding: 0px;
  list-style: none;
}
.item-intro-nav li{
  float: left;
  height: 100%;
  width: 120px;
  line-height: 38px;
  text-align: center;
  color: #E4393C;
}
.item-intro-nav li:first-child{
  background-color: #E4393C;
  color: #fff;
}
.item-intro-img{
  width: 100%;
}
.item-intro-img img{
  width: 40%;
  margin-left: 10%;
}
.item-intro-price{
	width: 40%;
	height: 200px;
	float: right;
	color: red;
	text-align: center;
}
.item-intro-price span{
	font-size: 24px;
}
/************* 商品参数 *************/
.item-param-container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: space-between;
}
.item-param-box {
  padding: 5px;
  padding-left: 30px;
  width: 240px;
  height: 36px;
  font-size: 14px;
  /* text-align: center; */
  /* background-color: #ccc; */
}
.item-param-title {
  color: #232323;
}
.item-param-content {
  color: #999;
}
.remarks-title {
  padding-left: 15px;
  height: 36px;
  font-size: 16px;
  font-weight: bolder;
  line-height: 36px;
  color: #666666;
  background-color: #F7F7F7;
}
.remarks-analyse-box {
  padding: 15px;
  display: flex;
  align-items: center;
}
.remarks-analyse-goods {
  margin-left: 15px;
  margin-right: 15px;
}
.remarks-analyse-num {
  font-size: 26px;
}
.remarks-analyse-title {
  font-size: 12px;
  line-height: 20px;
}
.remarks-bar {
  padding-left: 15px;
  height: 36px;
  line-height: 36px;
  color: #666666;
  background-color: #F7F7F7;
}
.remarks-bar span {
  margin-right: 15px;
}
.remarks-box {
  padding: 15px;
  display: flex;
  flex-direction: row;
  border-bottom: 1px #ccc dotted;
}
.remarks-user {
  width: 180px;
}
.remarks-user-name {
  padding-left: 15px;
}
.remarks-content-box {
  width: calc(100% - 180px);
}
.remarks-star {
  background-color: #fff;
}
.remarks-content {
  font-size: 14px;
  color: #232323;
  line-height: 28px;
}
.remarks-sub {
  margin-top: 15px;
  color: #ccc;
}
.remarks-time {
  margin-left: 15px;
}
.remarks-page {
  margin: 15px;
  display: flex;
  justify-content:flex-end;
}
/***************商品详情介绍和推荐侧边栏结束***************/
</style>

<style>
/* 改变便签页样式 */
.ivu-tabs-ink-bar {
  background-color: #E4393C !important;
}
.item-tabs > .ivu-tabs > .ivu-tabs-bar .ivu-tabs-tab{
  border-radius: 0px;
  color: #999;
  height: 38px;
  background: #F7F7F7;
}
.item-tabs > .ivu-tabs > .ivu-tabs-bar .ivu-tabs-tab-active{
  color: #fff;
  background-color: #E4393C;
}
.item-tabs > .ivu-tabs > .ivu-tabs-bar .ivu-tabs-tab-active:before{
  content: '';
  display: block;
  width: 100%;
  height: 1px;
  color: #fff;
  background: #F7F7F7;
  position: absolute;
  top: 0;
  left: 0;
}
.ivu-rate-star-full:before, .ivu-rate-star-half .ivu-rate-star-content:before {
  color: #E4393C;
}
</style>
