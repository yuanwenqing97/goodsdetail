<template>
  <div class="wrapper">
    <img src="../../../static/img/broadcast/background.jpg" alt="background" class="background"/>
    <div class="container">
      <div class="left">
        <div class="left-title">
          <div style="float: left;">
            <img src="../../../static/img/head.png" alt="avatar" class="user-avatar"/>
            <div class="left-title-content">
              <div style="font-size: 20px">大E定制|浙江省</div>
              <div style="font-size: 18px">主播暂无标签</div>
            </div>
          </div>
          <div style="float: right">
            <div style="margin-top: 20px; margin-right: 20px;">
              <el-button type="primary" @click="addFocus">关注</el-button>
              <div style="font-size: 14px; margin-top: 5px; margin-right: 5px; margin-left: -5px;">12500已关注</div>
            </div>
          </div>
          <div class="clear-fix"></div>
          <div class="video-wrapper">
            <img src="../../../static/img/freeback.png" alt="video" class="video"/>
            <img src="../../../static/img/broadcast/buttons.png" alt="buttons" class="buttons"/>
          </div>
        </div>
      </div>
      <div class="right">
        <div class="title">
          <div style="width:85px; border-bottom: 2px solid orange">主播推荐</div>
        </div>
        <div style="height: 440px;overflow-y:scroll;" class="scroll-box">
          <template v-for="(item,index) of items">
            <div :key="index" style="border-bottom: 1px solid grey;">
              <img src="../../../static/img/head.png" alt="item" style="width: 70px; height: 70px; margin: 10px">
              <div style="display: inline-block; ">
                <div style="width: 170px; font-size: 15px; margin: 10px 0;">{{item.title}}</div>
                <div style="margin-bottom: 5px;">
                  <span style="color: red;font-size: 18px;">￥{{item.priceNow}}</span>
                  <span style="font-size: 16px; margin-left: 30px;"><s>￥{{item.priceBefore}}</s></span>
                </div>
              </div>
            </div>
          </template>
        </div>
      </div>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
  import Footer from '@/components/footer/Footer';

  export default {
    name: 'shop-broadcast',
    components: {Footer},
    data () {
      return {
        items: [{
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }, {
          title: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          priceNow: 209,
          priceBefore: 319
        }]
      };
    },
    methods: {
      addFocus () {
        // 关注
      },
    }
  };
</script>

<style scoped>
  .container {
    /*background-color: #F6F6F6;*/
    width: 80%;
    height: 600px;
    margin: 20px auto;
  }

  .background {
    position: absolute;
    top: -30px;
    z-index: -1;
    width: 100%;
    height: 1080px;
  }

  .title {
    height: 60px;
    background-color: rgba(0, 0, 0, 0.6);
    padding-left: 10px;
    padding-top: 15px;
    /*font-weight: bold;*/
    font-size: 20px;
    color: white;
  }

  .left {
    width: 60%;
    height: 500px;
    margin-left: 5%;
    margin-right: 5%;
    margin-top: 50px;
    background-color: rgba(0, 0, 0, 0.6);
    color: white;
    float: left;
  }

  .left-title-content {
    display: inline-block;
    margin-left: 15px;
    margin-top: -10px;
  }

  .user-avatar {
    margin-left: 30px;
    margin-top: 20px;
    width: 50px;
    height: 50px;
    border-radius: 25px;
  }

  .right {
    width: 25%;
    height: 500px;
    margin-top: 50px;
    margin-left: 10px;
    background-color: white;
    float: left;
  }

  .clear-fix:after {
    clear: both;
    content: ".";
    display: block;
    height: 0;
    visibility: hidden;
  }

  .video-wrapper {
    background-color: black;
    width: 650px;
    height: 330px;
    margin-left: 15px;
    margin-top: 10px;
  }

  .video {
    width: 500px;
    height: 330px;
    position: relative;
    left: 30px;
  }

  .buttons {
    width: 600px;
    height: 50px;
    position: relative;
    left: 30px;
  }


  /*滚动条样式*/
  .scroll-box::-webkit-scrollbar { /*滚动条整体样式*/
    width: 4px; /*高宽分别对应横竖滚动条的尺寸*/
    height: 4px;
  }

  .scroll-box::-webkit-scrollbar-thumb { /*滚动条里面小方块*/
    border-radius: 5px;
    -webkit-box-shadow: inset 0 0 5px orange;
    background: rgba(0, 0, 0, 0.2);
  }

  .scroll-box::-webkit-scrollbar-track { /*滚动条里面轨道*/
    -webkit-box-shadow: inset 0 0 5px orange;
    border-radius: 0;
    background: rgba(0, 0, 0, 0.1);
  }

</style>

<style>
  .el-button--primary {
    background-color: orange !important;
    border-color: orange !important;
  }
</style>
