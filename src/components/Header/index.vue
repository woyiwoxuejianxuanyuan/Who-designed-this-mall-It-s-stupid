<template>
  <div class="header">
    <div class="headers">
      <div class="left">
        <p>天猫首页</p>
        <p><router-link to="/login">登录</router-link></p>
        <p>注册</p>
        <p>退出</p>
      </div>
      <div class="right">
        <ul class="uls">
          <li>
            <el-dropdown @visible-change="dropDownHover" class="lis">
              <span
                style="height:26px;display:block;"
                :class="[
                  'spa',
                  'el-dropdown-link',
                  {
                    'ho-color-red': showHover
                  }
                ]"
              >
                我的淘宝<i
                  style="color:#999;margin:0px;"
                  :class="[
                    'top',
                    'el-icon-caret-bottom',
                    'el-icon--right',
                    { trans: showHover }
                  ]"
                ></i>
              </span>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>已经买到的</el-dropdown-item>
                <el-dropdown-item>已经卖掉的</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </li>
          <li>
            <i style="color:#ff3306" class="el-icon-shopping-cart-1"></i>
            购物车
          </li>
          <li>
            <el-dropdown @visible-change="dropDownHoverles" class="lis">
              <span
                style="height:26px;display:block;"
                :class="[
                  'spa',
                  'el-dropdown-link',
                  {
                    'ho-color-red': showHovers
                  }
                ]"
              >
                收藏夹<i
                  style="color:#999;margin:0px;"
                  :class="[
                    'top',
                    'el-icon-caret-bottom',
                    'el-icon--right',
                    { trans: showHovers }
                  ]"
                ></i>
              </span>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>收藏的宝贝</el-dropdown-item>
                <el-dropdown-item>收藏的店铺</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </li>
          <li>
            <el-dropdown class="lis">
              <span
                style="height:26px;display:block;"
                :class="[
                  'spa',
                  'el-dropdown-link',
                  {
                    'ho-color-red': showHoveres
                  }
                ]"
              >
                <i style="color:#ff3306;margin:0px;" class="el-icon-mobile"></i
                >手机版
              </span>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>
                  <img class="imgs" src="../../assets/erweima.jpg" alt="" />
                </el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </li>
          <li>
            淘宝网
          </li>
          <li>
            <el-dropdown @visible-change="dropDownHoverles" class="lis">
              <span
                style="height:26px;display:block;"
                :class="[
                  'spa',
                  'el-dropdown-link',
                  {
                    'ho-color-red': showHoverles
                  }
                ]"
              >
                商家列表<i
                  style="color:#999;margin:0px;"
                  :class="[
                    'top',
                    'el-icon-caret-bottom',
                    'el-icon--right',
                    { trans: showHoverles }
                  ]"
                ></i>
              </span>
              <el-dropdown-menu class="elm" slot="dropdown">
                <title>
                  商家:
                </title>
                <el-dropdown-item v-for="item in data" :key="item.id"
                  ><router-link :to="item.paths">{{
                    item.name
                  }}</router-link></el-dropdown-item
                >
                <div class="line"></div>
                <title>
                  帮助:
                </title>
                <el-dropdown-item v-for="item in adata" :key="item.id"
                  ><router-link :to="item.paths">{{
                    item.name
                  }}</router-link></el-dropdown-item
                >
                <div class="line"></div>
              </el-dropdown-menu>
            </el-dropdown>
          </li>
          <li>
            <el-dropdown @visible-change="dropDownHoverless" class="lis">
              <span
                style="height:26px;display:block;"
                :class="[
                  'spa',
                  'el-dropdown-link',
                  {
                    'ho-color-red': showHoverless
                  }
                ]"
              >
                <i
                  style="color:#ff3306;margin:0px;"
                  :class="['top', 'el-icon-s-operation', 'el-icon--right']"
                ></i>
                网站导航<i
                  style="color:#999;margin:0px;"
                  :class="[
                    'top',
                    'el-icon-caret-bottom',
                    'el-icon--right',
                    { trans: showHoverless }
                  ]"
                ></i>
              </span>
              <el-dropdown-menu class="elms" slot="dropdown">
                <div class="block block1">
                <title class="titles">热点推荐 Hot</title>
                    <el-dropdown-item v-for="item in sitemap" :key="item.id"
                  ><router-link :to="item.paths">{{
                    item.name
                  }}</router-link></el-dropdown-item
                >
                </div>
                <div class="Verticalline"></div> 
                 <div class="block block2">
                 <title class="titles titles1">行业市场 Market</title>
                    <el-dropdown-item v-for="item in IndustryMarket" :key="item.id"
                  ><router-link :to="item.paths">{{
                    item.name
                  }}</router-link></el-dropdown-item
                >
                </div>
                <div class="Verticalline"></div> 
                <div class="block block3">
                <title class="titles titles2">服务指南 Help</title>
                    <el-dropdown-item v-for="item in service" :key="item.id"
                  ><router-link :to="item.paths">{{
                    item.name
                  }}</router-link></el-dropdown-item
                >
                </div>
              </el-dropdown-menu>
            </el-dropdown>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      count: "0",
      showHover: false,
      showHovers: false,
      showHoveres: false,
      showHoverles: false,
      showHoverless: false,
      data: [],
      adata: [],
      sitemap:[],
      IndustryMarket:[],
      service:[]
    };
  },
  methods: {
    dropDownHover(type) {
      console.log(type);
      this.showHover = type;
    },
    dropDownHovers(type) {
      this.showHovers = type;
    },
    dropDownHoveres(type) {
      this.showHoveres = type;
    },
    dropDownHoverles(type) {
      this.showHoverles = type;
    },
    dropDownHoverless(type) {
      this.showHoverless = type;
    }
  },
  mounted() {},
  created() {
    //请求商家支持商家的json
    this.$axios
      .get("/static/json/shoperlist.json")
      .then(res => {
        this.data = res.data;
      })
      .catch(reg => {
        console.log(reg);
      });
    //请求商家支持帮助的josn
    this.$axios
      .get("/static/json/shoperlist1.json")
      .then(res => {
        this.adata = res.data;
      })
      .catch(reg => {
        console.log(reg);
      });
        //请求网站导航的json
      this.$axios
      .get("/static/json/sitemaphot.json")
      .then(res => {
        this.sitemap = res.data;
        console.log(this.sitemap);
      })
      .catch(reg => {
        console.log(reg);
      });
      //请求网站导航行业市场的json
      this.$axios
      .get("/static/json/IndustryMarket.json")
      .then(res => {
        this.IndustryMarket = res.data;
        console.log(this.IndustryMarket);
      })
      .catch(reg => {
        console.log(reg);
      });
      //请求网站导航服务指南json
      this.$axios
      .get("/static/json/service.json")
      .then(res => {
        this.service = res.data;
        console.log(this.service);
      })
      .catch(reg => {
        console.log(reg);
      });
  }
};
</script>
<style scoped>
.hel {
  width: 20px;
  height: 30px;
  background: red;
}
.header {
  color: #999;
  font-size: 12px;
  width: auto;
  height: 26px;
  background: #f2f2f2;
  z-index: 99999;
  --webkit-transform: translate3d(0, 0, 0);
  border-bottom: 1px solid #e5e5e5;
}
.headers {
  width: auto;
  padding: 0 20%;
  height: 26px;
  display: flex;
  line-height: 26px;
  justify-content: space-between;
}
.left {
  display: flex;
  width: auto;
}
.left > p {
  padding: 0 4px;
  white-space: nowrap;
  cursor: pointer;
}
.left > p:hover {
  color: red;
  text-decoration: underline;
}
.ho-color-red {
  color: red;
  text-decoration: underline;
}
.uls {
  display: flex;
}
.uls > li {
  padding: 0 6px;
}
.uls > li:hover {
  color: red;
  text-decoration: underline;
  cursor: pointer;
}
.lis {
  color: #999;
  font-size: 12px;
}
.lis >>> .spa:hover {
  color: red;
  text-decoration: underline;
  cursor: pointer;
}
.lis:hover >>> .top {
  font-size: 4px;
  color: #999;
}
.lis .trans {
  transform: rotate(180deg);
  transition: all 1s ease 0s;
}
.imgs {
  width: 110px;
  height: 110px;
}
.elm {
  width: 200px;
  display: flex;
  flex-wrap: wrap;
}
.elm > li {
  padding: 0 14px;
  margin: 0 10px;
  text-align: center;
  height: 24px;
  line-height: 24px;
  font-size: 12px;
}
a {
  text-decoration: none;
  color: inherit;
}
title {
  display: block;
  width: 100%;
  padding: 0 20px;
  font-size: 14px;
  color: #666;
  font-weight: 700;
}
.line {
  width: 80%;
  height: 1px;
  border-bottom: 1px dashed black;
  margin: 0 10%;
  margin-bottom: 4px;
}
.elms {
  width: 1190px;
  display: flex;
  flex-wrap: wrap;
}
.block{
  padding: 0 10px;
  display: flex;
  flex-wrap: wrap;
}
.block>li{
    height: 24px;
  line-height: 24px;
  font-size: 12px;
}
.block1{
  width: 40%;
  margin: 0;
  padding: 0;
}
.block2{
  width: 30%;
}
.block3{
  width: 24%;
}
.titles{
  color: #f56a00;
  font-size: 16px;
  padding-bottom: 8px;
}
.titles1{
color: #2263d4}
.titles2{
  color: #666;
}
.Verticalline{
  height: auto;
  border-right: 1px solid #ccc;
}
 a{
 display: inline-block;
  line-height: 26px;
 }
</style>