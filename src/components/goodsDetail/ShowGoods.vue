<template>
  <div>
    <div class="item-detail-show">
      <div class="item-detail-left">
        <div class="item-detail-big-img">
          <img :src="goodsInfo.goodsImg[imgIndex]" alt="">
        </div>
        <div class="item-detail-img-row">
          <div class="item-detail-img-small" v-for="(item, index) in goodsInfo.goodsImg" :key="index" @mouseover="showBigImg(index)">
            <img :src="item" alt="">
          </div>
        </div>
      </div>
      <div class="item-detail-right">
        <div class="item-detail-title">
          <p>{{goodsInfo.title}}</p>
        </div>
        <div class="item-detail-tag">
          <p>
            <span v-for="(item,index) in goodsInfo.tags" :key="index">{{item}}</span>
          </p>
        </div>
        <div class="item-detail-price-row">
          <div class="item-price-left">
            <div class="item-price-row">
              <p>
                <span class="item-price-title">价格</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                <span>￥</span><span class="item-price">{{price.toFixed(2)}}</span>
              </p>
            </div>
            <div class="item-price-row">
              <p>
                <span class="item-price-title">促销价</span>&nbsp;&nbsp;&nbsp;
                <span class="item-price-full-cut" >￥189</span>
              </p>
            </div>
            <div class="item-price-row">
              <p>
                <span class="item-price-title">本店活动</span>
                <span class="item-price-full-dian" v-for="(item,index) in goodsInfo.promotion" :key="index">{{item}}</span>
                <span class="item-price-right">更多优惠</span>
              </p>
            </div>
            <div class="item-price-yun">
	          	<p>
	          		<span class="item-price-title">运费</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span>浙江嘉兴&nbsp;&nbsp;至&nbsp;&nbsp;徐州</span>
	          		<span>快递&nbsp;0.00</span>
	          	</p>
	          </div>
	          <div class="item-price-line">
	          	<p>月销量<span>7500+</span></p>
	          	<p>累计评价<span>16667</span></p>
	          </div>
	          <div class="item-goods-size">
	          	<span class="item-price-title" style="float: left;">尺码</span>
	          	<ul class="item-size">
	          		<li>S</li>
	          		<li>M</li>
	          		<li>L</li>
	          	</ul>
	          </div>
          </div>
        </div>
        <!-- 选择颜色 -->
        <div class="item-select">
          <div class="item-select-title">
            <p>颜色分类</p>
          </div>
          <div class="item-select-column">
            <div class="item-select-row" v-for="(items, index) in goodsInfo.setMeal" :key="index">
              <div class="item-select-box" v-for="(item, index1) in items" :key="index1" @click="select(index, index1)" :class="{'item-select-box-active': ((index * 3) + index1) === selectBoxIndex}">
                <div class="item-select-img">
                  <img :src="item.img" alt="">
                </div>
                <!--<div class="item-select-intro">
                  <p>{{item.intro}}</p>
                </div>-->
              </div>
            </div>
          </div>
        </div>
        <!-- 白条分期 -->
        <!--<div class="item-select">
          <div class="item-select-title">
            <p>白条分期</p>
          </div>
          <div class="item-select-row">
            <div class="item-select-class" v-for="(item,index) in hirePurchase" :key="index">
              <Tooltip :content="item.tooltip" placement="top-start">
                <span>{{item.type}}</span>
              </Tooltip>
            </div>
          </div>
        </div>-->
        <br>
        <div class="add-buy-car-box">
          <div class="add-buy-car">
          	<span class="item-price-title">数量</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <InputNumber :min="1" v-model="count" size="large"></InputNumber>
            <span>件</span>&nbsp;&nbsp;&nbsp;&nbsp;
            <span>库存：1274件</span>
            <br />
            <br />
            <Button class="item-buy-like"type="error" size="large" @click="addShoppingCartBtn()">立即购买</Button>
            <Button type="error" size="large" @click="addShoppingCartBtn()">加入购物车</Button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import store from '@/vuex/store';
import { mapState, mapActions } from 'vuex';
export default {
  name: 'ShowGoods',
  data () {
    return {
      price: 0,
      count: 1,
      selectBoxIndex: 0,
      imgIndex: 0
    };
  },
  computed: {
    ...mapState(['goodsInfo']),
    hirePurchase () {
      const three = this.price * this.count / 3;
      const sex = this.price * this.count / 6;
      const twelve = this.price * this.count / 12 * 1.0025;
      const twentyFour = this.price * this.count / 24 * 1.005;
      return [
        {
          tooltip: '无手续费',
          type: '不分期'
        },
        {
          tooltip: '无手续费',
          type: `￥${three.toFixed(2)} x 3期`
        },
        {
          tooltip: '无手续费',
          type: `￥${sex.toFixed(2)} x 6期`
        },
        {
          tooltip: '含手续费：费率0.25%起，￥0.1起×12期',
          type: `￥${twelve.toFixed(2)} x 12期`
        },
        {
          tooltip: '含手续费：费率0.5%起，￥0.1起×12期',
          type: `￥${twentyFour.toFixed(2)} x 24期`
        }
      ];
    }
  },
  methods: {
    ...mapActions(['addShoppingCart']),
    select (index1, index2) {
      this.selectBoxIndex = index1 * 3 + index2;
      this.price = this.goodsInfo.setMeal[index1][index2].price;
    },
    showBigImg (index) {
      this.imgIndex = index;
    },
    addShoppingCartBtn () {
      const index1 = parseInt(this.selectBoxIndex / 3);
      const index2 = this.selectBoxIndex % 3;
      const date = new Date();
      const goodsId = date.getTime();
      const data = {
        goods_id: goodsId,
        title: this.goodsInfo.title,
        count: this.count,
        package: this.goodsInfo.setMeal[index1][index2]
      };
      this.addShoppingCart(data);
      this.$router.push('/shoppingCart');
    }
  },
  mounted () {
    const father = this;
    setTimeout(() => {
      father.price = father.goodsInfo.setMeal[0][0].price || 0;
    }, 300);
  },
  store
};
</script>

<style scoped>
/******************商品图片及购买详情开始******************/
.item-detail-show {
  width: 80%;
  margin: 15px auto;
  display: flex;
  flex-direction: row;
  background-color: #fff;
}
.item-detail-left {
  width: 350px;
  margin-right: 30px;
}
.item-detail-big-img {
  width: 350px;
  height: 350px;
  overflow: hidden;
  box-shadow: 0px 0px 8px #ccc;
  cursor: pointer;
}
.item-detail-big-img img {
  width: 100%;
}
.item-detail-img-row {
  margin-top: 15px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.item-detail-img-small {
  width: 68px;
  height: 68px;
  box-shadow: 0px 0px 8px #ccc;
  cursor: pointer;
}
.item-detail-img-small img {
  width: 100%;
}
/*商品选购详情*/
.item-detail-right {
  display: flex;
  flex-direction: column;
}
.item-detail-title p {
  color: #666;
  font-size: 20px;
}
.item-detail-express {
  font-size: 14px;
  padding: 2px 3px;
  border-radius: 3px;
  background-color: #e4393c;
  color: #fff;
}
/*商品标签*/
.item-detail-tag {
  font-size: 12px;
  color: #F18B6A;
}
/*价格详情等*/
.item-detail-price-row {
  padding: 5px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.item-price-left {
	width: 600px;
  display: flex;
  flex-direction: column;
}
.item-price-title {
  color: #999999;
  font-size: 14px;
  margin-right: 15px;
}
.item-price-row {
  margin: 5px 0px;
}
.item-price {
  text-decoration: line-through;
}
.item-price-full-cut {
  color: #e4393c;
  font-size: 23px;
  cursor: pointer;
}
.item-price-full-dian{
	color: #C69360;
	cursor: pointer;
}
.item-price-right{
	color: #C69360;
	float: right;
	margin-right: 0;
	margin-top: 2px;
	cursor: pointer;
}
.item-remarks-sum {
  padding-left: 8px;
  border-left: 1px solid #ccc;
}
.item-remarks-sum p {
  color: #999999;
  font-size: 12px;
  line-height: 10px;
  text-align: center;
}
.item-remarks-num {
  line-height: 18px;
  color: #005eb7;
}
.item-select {
  display: flex;
  flex-direction: row;
  margin-top: 15px;
}
.item-select-title {
  color: #999999;
  font-size: 14px;
  margin-right: 15px;
}
.item-select-column {
  display: flex;
  flex-direction: column;
}
.item-select-row {
  display: flex;
  flex-direction: row;
  margin-bottom: 8px;
}
.item-select-box {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.item-select-img {
  width: 36px;
}
.item-select-box {
  padding: 5px;
  margin-right: 8px;
  background-color: #f7f7f7;
  border: 0.5px solid #ccc;
  cursor: pointer;
}
.item-select-box:hover {
  border: 0.5px solid #e3393c;
}
.item-select-box-active {
  border: 0.5px solid #e3393c;
}
.item-select-img img {
  width: 100%;
}
.item-select-intro p {
  margin: 0px;
  padding: 5px;
}
.item-select-class {
  padding: 5px;
  margin-right: 8px;
  background-color: #f7f7f7;
  border: 0.5px solid #ccc;
  cursor: pointer;
}
.item-select-class:hover {
  border: 0.5px solid #e3393c;
}
.add-buy-car-box {
  width: 100%;
}
.item-price-line{
	width: 100%;
	margin-top: 5px;
	padding: 5px;
	border-top: 1px solid gray;
	border-bottom: 1px solid gray;
	display: flex;
	justify-content: space-around;
}
.item-price-line span{
	color: #E997A1;
}
.item-goods-size{
	width: 300px;
	height: 30px;
	margin-top:5px ;
	line-height: 30px;
}
.item-size{
	width: 120px;
	height: 30px;
	display: flex;
	justify-content: space-between;
	float: left;
	margin-left: 27px;
}
.item-size li{
	width: 30px;
	height: 30px;
	text-align: center;
	font-weight: bold;
	border: 1px solid black;
}
.item-size li:hover{
	border: 2px solid red;
	cursor: pointer;
}
.item-buy-like{
	border: 1px solid red;
	color: red;
	background: white;
	margin-right: 20px;
}
/******************商品图片及购买详情结束******************/
</style>
