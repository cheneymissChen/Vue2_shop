<template>
  <div>
    <img src="../../assets/mycenter_bg.png" class="mycenter_bg" />
    <section class="page">
      <div class="nav_container">
        <ul class="nav_list">
          <li class="nav_item"
            v-for="(item,index) in tabs"
            @click="toggle(index,item.type)"
            :class="{active:active==index}"
            :key="index"
          >{{item.view}}</li>
        </ul>
      </div>

      <div class="performance_wrap">
        <div class="performance_top">
          <div class="performance_time">2020年3月</div>
          <div class="result_show">
            <div class="performance_title">业绩说明</div>
            <img src="../../assets/skip.png" class="skip" />
          </div>
        </div>
        <ul class="performance_container">
          <li class="performance_contaxt">
            <div class="performance_number">3365</div>
            <div class="performance_money">签约金额/元</div>
          </li>
          <span class="divid_line">丨</span>
          <li class="performance_contaxt">
            <div class="performance_number">1243</div>
            <div class="performance_money">签约门店/家</div>
          </li>
          <span class="divid_line">丨</span>
          <li class="performance_contaxt">
            <div class="performance_number">2634</div>
            <div class="performance_money">续费金额/元</div>
          </li>
        </ul>
      </div>
      <!-- 点击tab切换我的团队与业绩两个组件间 -->
      <component :is="currentView"></component>

    </section>
  </div>
</template>

<script>
//我的团队组件
import team from "components/common/team";
//业绩共用组件
import performance from "components/common/performance";


export default {
  data() {
    return {
      active:0,//默认第一个
      currentView:'team',//默认第一个高亮显示
      tabs:[
        {
          type:'performance',
          view:'我的业绩'
         
        },
        {
          type:'team',
          view:'团队业绩'
        }
      ]
    };
  },
  methods: {
    toggle(i,v) {//点击tab切换相应的组件
      this.active=i;
      this.currentView=v;
    },

  
  },
  components: {
    team,
    performance
  }
};
</script>

<style lang="scss" type="text/scss" scoped>
@import "../../common/style/mixin";
html{
  background: rgb(246,245,248);
}
.mycenter_bg {
  height: 0.4rem;
  width: auto;
  height: auto;
  width: 100%;
  max-height: 100%;
}
.nav_container {
  width: 46%;
  position: absolute;
  top: 7%;
  left: 28%;
  height: 80px;
  line-height: 80px;
  margin: 0 auto;
 

  .nav_list {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    background: #ffffff;
  }
  .nav_item {
    width: 50%;
    height: 100%;
    background: #ffffff;
    color: #333333;
    text-align: center;
     font-size: 30px;
  }
  .active {
    width: 50%;
    height: 100%;
    background: rgb(0, 219, 172);
    color: #ffffff;
    font-size: 30px;
    font-weight: bold;
    text-align: center;
  }
}

/*业绩说明  */
.performance_wrap {
  width: 96%;
  height: 240px;
  background: #ffffff;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
  margin-top: 60px;
  padding: 0px 20px ;
  border-radius: 16px;
}
.performance_top {
  width: 100%;
  height: 100px;
  line-height: 100px;
  border-bottom: 1px #ededed solid;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.performance_time{
  padding: 0px 20px;
  font-size: 28px;
}
.result_show {
  width: 120px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.performance_title {
  font-size: 24px;
  color: #5fd7af;
}
.skip {
  width: 10px;
  height: 20px;
  line-height: 20px;
  margin: 40px 0px;
}
.performance_container {
  height: 140px;
  line-height: 40px;
  width: 100%;
  display: flex;
  flex-direction: row;
  padding: 10px 0px;
}
.performance_contaxt {
  width: 33%;
  text-align: center;
}
.performance_number {
  text-align: center;
  height: 40px;
  line-height: 40px;
  color: #333333;
  font-family: PingFang SC;
  font-size: 36px;
  font-weight: 400;
}
.performance_money {
  color: #888888;
  font-size: 28px;
  margin-top: 10px;
  font-family:PingFang SC;
   font-weight:400;
}
.divid_line {
  height: 0.4rem;
  color: #ededed;
  font-size: 0.2rem;
  margin: 0.08rem 0rem;
}

</style>
