<template>
  <div>
    <Sreach></Sreach>
    <!-- <GoodsListNav></GoodsListNav> -->
    <div class="container">
      <div>找到相关店铺882975</div>
      <div class="conten">
        <div class="box">
          <ul>
            <li>默认排序</li>
            <li>销量</li>
            <li>信用</li>
          </ul>
        </div>
        <div class="box2">
          <el-dropdown trigger="click">
            <span class="el-dropdown-link">
              店铺类型
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
          <el-dropdown trigger="click">
            <span class="el-dropdown-link">
              所在地
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
          <el-dropdown trigger="click">
            <span class="el-dropdown-link">
              制定筛选
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
          <el-dropdown trigger="click">
            <span class="el-dropdown-link">
              好评率
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
        </div>
      </div>
      <div class="conten">
        <el-checkbox-group v-model="checkList">
          <el-checkbox label="收藏和购买过"></el-checkbox>
          <el-checkbox label="特色店铺"></el-checkbox>
        </el-checkbox-group>
      </div>
      <div class="main" v-for="(item, index) in shopListItem" :key="index" @click="tiDetile()">
        <div class="main_left">
          <div class="left_a">
            <img :src="item.img" alt>
            <div class="left_v">
              <p class="title" v-text="item.title"></p>卖家
              <span class="name" v-text="item.name"></span>
              <span class="chengshi" v-text="item.chengshi"></span>
              主营
              <p class="name" v-text="item.type"></p>
            </div>
          </div>
          <div class="left_bottom">
            <p>
              销量
              <span class="name" v-text="item.xiaoliang"></span>
              共
              <span class="name" v-text="item.number"></span>件宝贝
            </p>好评率
            <span v-text="item.pinlu"></span>
          </div>
        </div>
        <div class="main_right">
          <div class="right_list">
            <img :src="item.image" alt>
            <div v-text="item.price"></div>
          </div>
          <div class="right_list">
            <img :src="item.image" alt>
            <div v-text="item.price"></div>
          </div>
          <div class="right_list">
            <img :src="item.image" alt>
            <div v-text="item.price"></div>
          </div>
          <div class="right_list">
            <img :src="item.image" alt>
            <div v-text="item.price"></div>
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
  name: "GoodsList",
  beforeRouteEnter(to, from, next) {
    window.scrollTo(0, 0);
    next();
  },
  data() {
    return {
      currentPage3: 5,
      shopListItem: [
        {
          id: 0,
          img: "../../../static/img/shop/miao.gif",
          title: "汤圆是买衣服的",
          name: "翻跟斗的汤圆",
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
          title: "汤圆是买衣服的",
          name: "翻跟斗的汤圆",
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
          title: "汤圆是买衣服的",
          name: "翻跟斗的汤圆",
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
          title: "汤圆是买衣服的",
          name: "翻跟斗的汤圆",
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
          title: "汤圆是买衣服的",
          name: "翻跟斗的汤圆",
          chengshi: "浙江 宁波",
          type: "女 宽松百搭 显瘦秋冬! 新款纯色 长袖 外套",
          xiaoliang: "15680",
          number: "598",
          pinlu: "98%",
          image: "../../../static/img/shop/images5.gif",
          price: "￥85元"
        }
      ],
      sreachItem: "",
      isAction: [true, false, false],
      icon: ["arrow-up-a", "arrow-down-a", "arrow-down-a"],
      goodsTool: [
        { title: "综合", en: "sale" },
        { title: "评论数", en: "remarks" },
        { title: "价格", en: "price" }
      ],
      checkList: ["选中且禁用", "复选框 A"]
    };
  },
  computed: {
    ...mapState(["asItems", "isLoading"]),
    ...mapGetters(["orderGoodsList"])
  },
  methods: {
    ...mapActions(["loadGoodsList"]),
    ...mapMutations(["SET_GOODS_ORDER_BY"]),
    orderBy(data, index) {
      console.log(data);
      this.icon = ["arrow-down-a", "arrow-down-a", "arrow-down-a"];
      this.isAction = [false, false, false];
      this.isAction[index] = true;
      this.icon[index] = "arrow-up-a";
      this.SET_GOODS_ORDER_BY(data);
    },
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
    tiDetile(){
        this.$router.push({path:"/item"});
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
.conten {
  display: flex;
  justify-content: space-between;
  background-color: #eaeaea;
  border: 1px solid #cccccc;
  height: 40px;
}
ul,
li {
  padding: 0;
  margin: 0;
  list-style: none;
}
.box > ul > li {
  display: inline-block;
  font-size: 16px;
}
.box > ul {
  height: 40px;
  line-height: 40px;
}
.box2 {
  height: 40px;
  line-height: 40px;
}
.box > ul > li:nth-child(1) {
  color: red;
}
.el-dropdown-link {
  cursor: pointer;
  color: black;
}
.el-icon-arrow-down {
  font-size: 12px;
}
.demonstration {
  display: block;
  color: #8492a6;
  font-size: 14px;
  margin-bottom: 20px;
}
.container {
  margin: 15px auto;
  width: 85%;
  min-width: 1000px;
}
.text-danger {
  color: #a94442;
}
.seckill-price {
  margin-right: 5px;
  font-size: 25px;
  font-weight: bold;
}
.goods-box {
  display: flex;
}
/* 商品栏 */
.main {
  display: flex;
  justify-content: space-between;
  height: 200px;
  border-bottom: 1px solid #ccc;
  margin-top: 20px;
  padding-bottom: 20px;
}
.main_left {
  width: 400px;
}
.left_a {
  width: 400px;
  /* border: 1px solid red; */
  display: flex;
  justify-content: space-between;
}
.left_bottom {
  width: 400px;
  padding-top: 70px;
  /* border: 1px solid red; */
}
.title {
  color: black;
  font-size: 14px;
  font-weight: 600;
}
.name {
  color: black;
  font-weight: 600;
}
.main_right {
  width: 650px;
  display: flex;
  justify-content: space-between;
  /* border: 1px slateblue solid; */
}
.block {
  margin: 0 auto;
  width: 45%;
}
</style>
