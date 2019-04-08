<template>
  <div>
    <Sreach></Sreach>
    <div class="container">
      <div>
        全部>
        <input type="text" placeholder="女装">
      </div>
      <div class="box">
        <div class="conten">
          <div class="pinpai">品牌</div>
          <div class="banner">
            <img src="../../../static/img/shop/banner.gif" alt>
          </div>
          <div class="gengduo">
            <span>+多选</span>
            <span>
              <el-dropdown trigger="click">
                <span class="el-dropdown-link">
                  更多
                  <i class="el-icon-arrow-down el-icon--right"></i>
                </span>
                <el-dropdown-menu slot="dropdown">
                  <el-dropdown-item icon="el-icon-plus">黄金糕</el-dropdown-item>
                  <el-dropdown-item icon="el-icon-circle-plus">狮子头</el-dropdown-item>
                  <el-dropdown-item icon="el-icon-circle-plus-outline">螺蛳粉</el-dropdown-item>
                  <el-dropdown-item icon="el-icon-check">双皮奶</el-dropdown-item>
                  <el-dropdown-item icon="el-icon-circle-check-outline">蚵仔煎</el-dropdown-item>
                </el-dropdown-menu>
              </el-dropdown>
            </span>
          </div>
        </div>
        <div class="conten_ut">
          <span>
            <i class="el-icon-arrow-down el-icon-caret-right"></i>
            品牌女装
          </span>
          <span>连衣裙</span>
          <span>女士老年服装</span>
          <span>大码女装</span>
          <span>女生T恤</span>
          <span>女生毛衣</span>
          <span>女生衬衫</span>
          <span>女生羽绒服</span>
        </div>
        <div class="conten_change">
          <span>
            <i class="el-icon-arrow-down el-icon-caret-right"></i>
            其他分类
          </span>
          <span>女T恤</span>
        </div>
        <div class="conten_footer">
          <span>袖长</span>
          <span>长袖</span>
          <span>短袖</span>
          <span>无袖</span>
          <span>七分袖</span>
          <span>五分袖</span>
          <span>九分袖</span>
          <span>长袖被肩</span>
        </div>
       
      </div>
       <div class="goods-list-tool">
          <ul>
            <li v-for="(item,index) in goodsTool" :key="index" @click="orderBy(item.en, index)">
              <span :class="{ 'goods-list-tool-active': isAction[index]}">
                {{item.title}}
                <Icon :type="icon[index]"></Icon>
              </span>
            </li>
          </ul>
        </div>

        <div class="main_box">
          <div class="main" v-for="(item,index) in shopListItem" :key="index">
            <div class="main_top">
              <img class="image" :src="item.image" alt>
              <img class="img" :src="item.img" alt>
              <img class="img" :src="item.img" alt>
              <img class="img" :src="item.img" alt>

              <p class="price" v-text="item.price"></p>
              <p class="title" v-text="item.title"></p>
              <p class="name" v-text="item.name"></p>
              <p>
                月成交
                <span v-text="item.number"></span>
                评价
                <span>{{item.xiaoliang}}</span>
              </p>
            </div>
          </div>
        </div>
              <div class="block">
        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page.sync="currentPage3"
          :page-size="100"
          layout="prev, pager, next, jumper"
          :total="1000"
        ></el-pagination>
      </div>
      <div class="bottom">
        <span>您是不是想找</span> |
        <span>女装</span> |
        <span>短袖</span> |
        <span>长袖</span> |
        <span>长袖春装</span> |
        <span>大码服装</span> |
        <span>衣服</span> |
        <span>连衣裙</span> |
      </div>
      <div class="main_box">
        <div class="main" v-for="(item,index) in footer_list" :key="index">
            <div class="main_top">
              <img class="image" :src="item.image" alt>
                <p>
             
                <span class="price" v-text="item.price"></span>
                   月成交
                <span v-text="item.number"></span>
              </p>
              <p class="title" v-text="item.title"></p>
              <p class="name" v-text="item.name"></p>
            
            </div>
          </div>
      </div>
    </div>
        <Footer></Footer>
    <Spin size="large" fix v-if="isLoading"></Spin>
  </div>
</template>

<script>
import Sreach from "@/components/Sreach";
import GoodsListNav from "@/components/nav/GoodsListNav";
import GoodsClassNav from "@/components/nav/GoodsClassNav";
import Footer from "@/components/footer/Footer";
import store from "@/vuex/store";
import { mapState, mapActions, mapGetters, mapMutations } from "vuex";
export default {
  // name: 'shop-items',
  beforeRouteEnter(to, from, next) {
    window.scrollTo(0, 0);
    next();
  },
  data() {
    return {
      currentPage3: 5,
      sreachItem: "",
      footer_list:[{
          id: 0,
          img: "../../../static/img/shop/miao.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images1.gif",
          price: "￥85元"
        },{
          id: 1,
          img: "../../../static/img/shop/miao.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images1.gif",
          price: "￥85元"
        },{
          id: 2,
          img: "../../../static/img/shop/miao.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images1.gif",
          price: "￥85元"
        },{
          id: 3,
          img: "../../../static/img/shop/miao.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images1.gif",
          price: "￥85元"
        },{
          id: 4,
          img: "../../../static/img/shop/miao.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images1.gif",
          price: "￥85元"
        },],
      isAction: [true, false, false],
      icon: ["arrow-up-a", "arrow-down-a", "arrow-down-a", "arrow-down-a"],
      goodsTool: [
        { title: "综合", en: "sale" },
        { title: "评论数", en: "remarks" },
        { title: "价格", en: "price" },
        { title: "销量", en: "xiaoliang" }
      ],
      shopListItem: [
        {
          id: 0,
          img: "../../../static/img/shop/miao.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images1.gif",
          price: "￥85元"
        },
        {
          id: 2,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 3,
          img: "../../../static/img/shop/dinghzi.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images3.gif",
          price: "￥85元"
        },
        {
          id: 4,
          img: "../../../static/img/shop/whiter.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images4.gif",
          price: "￥85元"
        },
        {
          id: 5,
          img: "../../../static/img/shop/chin.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images5.gif",
          price: "￥85元"
        },
        {
          id: 6,
          img: "../../../static/img/shop/chin.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images5.gif",
          price: "￥85元"
        },
        {
          id: 7,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 8,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },

        {
          id: 9,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },

        {
          id: 10,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 11,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 12,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 13,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 14,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        },
        {
          id: 15,
          img: "../../../static/img/shop/guoguo.gif",
          title: "春秀高腰显瘦阔脱裤",
          name: "怡情旗舰店",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images2.gif",
          price: "￥85元"
        }
      ]
    };
  },
  computed: {
    ...mapState(["asItems", "isLoading"]),
    ...mapGetters(["orderGoodsList"])
  },
  methods: {
      handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
    ...mapActions(["loadGoodsList"]),
    ...mapMutations(["SET_GOODS_ORDER_BY"]),
    orderBy(data, index) {
      console.log(data);
      this.icon = [
        "arrow-down-a",
        "arrow-down-a",
        "arrow-down-a",
        "arrow-down-a"
      ];

      this.isAction = [false, false, false];
      this.isAction[index] = true;
      this.icon[index] = "arrow-up-a";
      this.SET_GOODS_ORDER_BY(data);
    }
  },
  created() {
    this.loadGoodsList();
  },
  mounted() {
    this.sreachItem = this.$route.query.sreachData;
  },
  components: {
    Sreach,
    GoodsListNav,
    GoodsClassNav,
    Footer
  },
  store
};
</script>

<style scoped>
.container {
  margin: 15px auto;
  width: 65%;
  min-width: 1000px;
}
.box {
  background-color: #eaeaea;
  border: 1px solid #cccccc;

  /* height: 80px; */
}
.conten {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid #cccccc;
}
.banner {
  width: 600px;
  height: 100px;
}
.banner > img {
  width: 100%;
  height: 100%;
}
.conten_ut {
  display: flex;
  justify-content: space-between;
  width: 480px;
  /* border: 1px solid red; */
  flex-wrap: wrap;
  margin-top: 10px;
  border-bottom: 1px solid #cccccc;
}
.conten_ut > span {
  width: 80px;
  color: black;
  height: 30px;
  line-height: 30px;
  /* border: 1px solid red; */
}
.conten_change {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
  width: 160px;
  border-bottom: 1px solid #cccccc;
}
.conten_change > span {
  width: 80px;
}
.conten_footer {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
  border-bottom: 1px solid #cccccc;
  width: 600px;
}
.goods-list-tool {
  width: 100%;
  height: 38px;
  border: 1px solid #ccc;
  background-color: #f1f1f1;
}
.goods-list-tool ul {
  /* padding-left: 15px; */
  list-style: none;
}
.goods-list-tool li {
  cursor: pointer;
  float: left;
}
.goods-list-tool span {
  padding: 5px 8px;
  border: 1px solid #ccc;
  border-left: none;
  line-height: 36px;
  background-color: #fff;
}
.goods-list-box {
  margin-left: 15px;
  width: calc(100% - 215px);
}
.goods-list-tool span:hover {
  border: 1px solid #e4393c;
}
.goods-list-tool i:hover {
  color: #e4393c;
}
.goods-list-tool-active {
  color: #fff;
  border-left: 1px solid #ccc;
  background-color: #e4393c !important;
}
.main_box {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.main {
  border: 1px solid #ccc;
  width: 170px;
  display: inline-block;
  margin-top: 10px;
}
.image {
  width: 170px;
}
.price {
  color: red;
  font-size: 14px;
  font-weight: 600;
}
.img {
  width: 30px;
}
.title {
  color: black;
  font-size: 12px;
  font-weight: 600px;
}
.main_top > p > span:nth-child(1) {
  color: #e4393c;
}
.main_top > p > span:nth-child(2) {
  color: teal;
  float:right;
}
.block{
  width: 50%;
  margin: 0 auto;
}
.bottom{
border: 1px solid #cccccc;
height: 30px;
line-height: 30px;
margin-top: 10px;
}
</style>
