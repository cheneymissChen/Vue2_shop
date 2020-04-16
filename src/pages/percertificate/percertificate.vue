<template>
    <div class="percertificate_container">
     <header class="user-head">
      <i class="iconfont icon-left" @click="goBack"></i>
      <span style="font-size:34px;font-weight:bold;height:110px;line-height:110px;">业绩说明</span>
      <i class="iconfont icon-More" ></i>
    </header>
    <section>
        <div class="account_wrap">
           <div class="account_container">

               · 签约金额：admin审批通过的门店签订合同时的签约金额（不包含未回款金额），案例：合同签约了3万，但门店只缴纳了1万，admin通过了，签约金额显示3万；<br>

             <div class="earn_wrap">  · 签约门店：admin审批通过的签约门店数；<br></div>

               
             <div class="earn_wrap">  · 续费金额：审批通过的门店（累计充值金额-合同签订金额）大于等于签约金额之和；<br></div>

             <div class="earn_wrap"> 
               特别说明：<br>

               已知A门店签约3万实际缴纳3万，累计充值5万。  B门店签约3万实际缴纳2万，但是admin同意审核，累计充值2万5。<br>

               续费金额只计算A门店5万-3万=2万，判断条件A门店累计充值5万＞合同签订3万，B门店累计充值2.5万小于合同签约3万，不计算在内。<br>
                                           
            </div>
           </div>   
           </div>
    </section>







    </div>
</template>
<script>
export default {
    data(){
        return{

        }

    },
    methods:{
     goBack(){
         this.$router.go(-1);
     }
    }
    
}
</script>
<style lang="scss" scoped>
@import "../../common/style/mixin";
.percertificate_container {
  background: #f7f7f7;
  padding-bottom: 10%;
  .user-head {
    display: flex;
    justify-content: space-between;
    // @include fj;
    width: 100%;
    height: 120px;
    padding: 0 20px;
    line-height: 88px;
    font-size: 30px;
    // @include boxSizing;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    border-bottom: 10px #f7f7f7 solid;
    background: #ffffff;
    .iconfont {
      font-size: 54px;
      height: 110px;
      line-height: 110px;
          }
  }
    .account_wrap{
        display:flex;
        flex-direction: column;
        width: 100%;
        height: 100%;
   
    .account_container{
        width: 80%;
        line-height: 54px;
        font-size: 28px ; 
        margin: 40px auto;
        color: #333333;
        font-family:PingFang SC;
        font-weight:400;
    
  .earn_wrap{
       margin: 30px 0px
    }
    }
     }
}

</style>