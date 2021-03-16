<template>
  <div class="login">
    <p>{{ text }}</p>
    <div class="login_page">
      <form action="" id="login" name="login" method="GET">
        <div class="username">
          <span>{{ $t("login.placeholder.account") }}：</span>
          <input type="text" name="username" id="login" />
          <div class="feedback"></div>
        </div>
        <div class="password">
          <span>{{ $t("login.placeholder.password") }}：</span>
          <input type="password" name="password" id="login"/>
          <div class="feedback"></div>
          </div>
      </form>
    </div>
    <p @click="fetchLinkage">{{ $t("login.title")}}</p>
  </div>
</template>

<script>
import linkage from "../api/linkage";
export default {
  data() {
    return {
      text: window.i18n.t("login.title"),
    };
  },
  created(){
    window.token = "";
  },
  methods: {
    // 查询存储计划
    fetchLinkage() {
      let self = this;
      let param = {
        token:"ba82240bb5988594b5e7d68f11ccff22"
      };
      linkage.fetch_linkage(param).then((rv) => {
        console.log(rv)
        if (rv.code == 0) {
          console.log(rv);
        } else {
          self.$message({
            message: self.$errorMessage(rv.code),
            type: "error",
          });
        }
      });
    },
  },
};
</script>

<style lang="scss">
.login {
  p {
    color: red;
  }
}
input{
  border: 1px solid black;
}
</style>
