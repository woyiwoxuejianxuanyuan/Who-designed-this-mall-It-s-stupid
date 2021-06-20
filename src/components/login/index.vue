<template>
  <div class="main">
    <div>
      <img
        src="https://www.iliangcang.com/images/nlicon.png"
        style="margin-bottom:60px;"
      />
      <input
        id="mobile"
        name="mobile"
        v-model="phone"
        type="number"
        placeholder="输入手机号"
        class="inp"
      />
      <div class="box">
        <input
          class="yanzheng"
          v-model="code"
          name="code"
          value=""
          placeholder="输入验证码"
        />
        <button
          type="button"
          class="getcode"
          :disabled="disabled"
          @click="sendCode"
        >
          {{ btntxt }}
        </button>
      </div>
      <button
        type="submit"
        value="登录"
        class="loginBtn"
        @click="login"
        style="border-radius: 4px;font-weight: normal;"
      >登录</button>
      <router-link to="">更多登录方式 ></router-link>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      disabled: false,
      time: 0,
      code:'',
      phonecode:'1',
      btntxt: "获取验证码",
        phone: this.phone
    };
  },
  methods: {
    //获取验证码检测input框
    sendCode() {
      var reg = 11 && /^((13|14|15|17|18)[0-9]{1}\d{8})$/;
      if (this.phone == "") {
        alert("请输入手机号码");
      } else if (!reg.test(this.phone)) {
        alert("手机格式不正确");
      } else {
        this.time = 60;
        this.disabled = true;
        this.timer();
        //请求验证码
        /*axios.post(url).then(
                        res=>{
                        this.phonecode=res.data;
                    })*/
      }
    },
    //点击登录按钮触发登录
    login(){
      if(this.code == ""){
        alert("请输入验证码")
      }else if(this.code!==this.phonecode){
        alert("请输入正确的验证码")
      }else{
        this.$router.push({ path:'/',query:{id:'123',name:'不是浮浮',logininfo:true} })
      }
    },
    //验证码倒计时
    timer() {
      if (this.time > 0) {
        this.time--;
        this.btntxt = this.time + "s后重新获取";
        setTimeout(this.timer, 1000);
      } else {
        this.time = 0;
        this.btntxt = "获取验证码";
        this.disabled = false;
      }
    }
  }
};
</script>
<style scoped>
a {
  text-decoration: none;
  color: #000;
}
.box {
  position: relative;
  padding-top: 22px;
}
.main {
  text-align: center;
  background-color: #fff;
  border-radius: 20px;
  width: 300px;
  height: 350px;
  position: absolute;
  left: 50%;
  top: 30%;
  transform: translate(-50%, -50%);
}
.inp {
  border: 0;
  border-bottom: solid 1px #000;
  font-size: 18px;
  width: 265px;
  height: 34px;
  background: url("https://www.iliangcang.com/images/nlphone.png") no-repeat 0px
    6px;
  padding-left: 35px;
}
.yanzheng {
  border: 0;
  border-bottom: solid 1px #000;
  font-size: 18px;
  width: 137px;
  height: 34px;
  float: left;
  background: url("https://www.iliangcang.com/images/nlcode.png") no-repeat 2px
    8px;
  padding-left: 35px;
}
.getcode {
  border: solid 1px #000;
  height: 35px;
  line-height: 34px;
  width: 110px;
  font-size: 16px;
  margin-left: 12px;
  border-radius: 4px;
  color: #333;
  float: right;
  cursor: pointer;
}
.loginBtn {
  cursor: pointer;
  width: 300px;
  height: 50px;
  border: 0;
  background: #25292e;
  font-size: 18px;
  font-weight: bold;
  color: #ffffff;
  margin-top: 9px;
  margin-bottom: 30px;
}
</style>