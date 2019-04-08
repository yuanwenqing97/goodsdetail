<template>
  <div>
    <div class="container">
      <i-input v-model="sreachData" size="large" class="sreach" placeholder="输入商品/品牌/店铺">
      <img slot="append" class="image" src="../../static/img/nav/店铺_03.jpg"/>
     
      </i-input>
      <Tag v-for="(item, index) in promotionTags" :key="index" closable  @on-close="closeTags(index)"><span @click="selectTags(index)">{{item}}</span></Tag>
     <router-link to="/shop">
        搜索
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sreach',
  data () {
    return {
    };
  },
  methods: {
    closeTags (index) {
      this.promotionTags.splice(index, 1);
    },
    selectTags (index) {
      this.sreachData = this.promotionTags[index];
    },
    sreach () {
      this.$router.push({path: '/goodsList', query: { sreachData: this.sreachData }});
    }
  }
};
</script>

<style scoped>
.container {
  padding-top: 15px;
  margin: 0px auto;
  margin-bottom: 15px;
  width: 460px;
}
.sreach {
  margin: 5px 0px;
}
.image {
  line-height: 0.5;
  padding: -3px -10px;
}
</style>
