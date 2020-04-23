<template>
    <div class="center_container">
         <m-header :mTitle="'个人中心'"></m-header>
         <div class="mine">我的</div>
         <div class="portrait_wrap">
              
          <div class="portrait">
           <img src="../../assets/head_shot.png" class="head_shot">
          </div>
          <div class="user_wrap">
          <div class="user_title">殷伟业</div>
          <div class="user_info">标准用户</div>
          </div>
          <div class="account_wrap">
              <div class="account_message">账户管理</div>
                <img src="../../assets/back.png" class="back">
          </div>
         </div>
     <section>
        <div class="earn_wrap">
            <div class="order_wrap">
                 <img src="../../assets/myorder.png" class="incon">
                 <div class="order_title">我的订单</div>
            </div>
             <div class="order_wrap">
                 <img src="../../assets/personal.png" class="incon">
                 <div class="order_title">个人资料</div>
            </div>
        </div>

     
        <div class="earn_wrap">
            <div class="order_wrap">
                 <img src="../../assets/address.png" class="incon">
                 <div class="order_title">地址管理</div>
            </div>
             <div class="order_wrap">
                 <img src="../../assets/changepassword.png" class="incon">
                 <div class="order_title">修改密码</div>
            </div>
        </div>
     </section>
    <footer>
        <div class="log_out" @click="userLogout">退出登录</div>
    </footer>

    </div>
</template>
<script>
  import mHeader from 'components/common/m-header'
   import {getUserInfo,logout} from "../../service/getData";
export default {
    data() {
            return {
              
            }
        },
    methods:{
          userLogout(){
                logout().then(()=>{
                    this.$router.push('./user')
                })
            },
    },
    components:{
        mHeader
    }
}
</script>
<style lang="scss" scoped>
  .center_container{
          background: rgb(246,245,248);
          .mine{
              position: absolute;
              right: 40px;
              top:45px;
              font-family:PingFang SC;
              font-weight:bold;
              color:rgba(51,51,51,1);
              font-size: 28px;
          }
    .portrait_wrap{
         display: flex;
         flex-direction: row;
          height:100px;
          padding: 50px 30px;
          background:linear-gradient(90deg,rgba(255,160,10,1) 0%,rgba(255,102,27,1) 100%);
        
    .portrait{
         width: 100px;
         height: 100px;
         background: #ffffff;
         border-radius: 50%;
       .head_shot{
           width: 100%;
           height: 100%;    
           border-radius: 50%;
       }
    }
    .user_wrap{
        display: flex;
        flex-direction: row;
        margin: 0 24% 0 4%;
         .user_title{
        height: 100px;
        line-height: 100px;
        font-size: 36px;
        color: #FFFFFF;
        margin-right: 16px;
    }  
     .user_info{
        width: 120px;
        height: 40px;
        line-height: 40px;
        background: #3333;
        border-radius: 10px;
        color: #fff;
        text-align: center;
        margin: 30px 0px;
    }
    }
   
   
    .account_wrap{
        display: flex;
        flex-direction: row;
    }
    .account_message{
        height: 100px;
        line-height: 100px;
        color: #fff;
        font-size:28px;
        font-family:PingFang SC;
        
    }
    .back{
        width: 20px;
        height: 20px;
        margin: 40px 10px;
    }
    }
      .earn_wrap{
          width: 90%;
          height: 260px;
          text-align: center;
          display: flex;
          flex-direction: row;
          margin: 40px auto;
          justify-content: space-between;
          
          .order_wrap{
              width: 48%;
              height: 100%;
              display: flex;
              flex-direction: column;
              justify-content: space-between;
              text-align: center;
              background: #FFFFFF;
            .incon{
                width: 18%;
                height: 22%;
                margin: 0px auto;
                margin-top: 90px;
                
            }
          }
          .order_title{
              height: 100px;
              font-size: 28px;
          }
      }
    .log_out{
        width: 90%;
        height: 80px;
        line-height: 80px;
        color: #FFFFFF;
        background: #FF9D11;
        text-align: center;
        border-radius: 10px;
        position: fixed;
        left: 6%;
        bottom: 8%;
        font-size: 32px;
        font-weight: bold;
    }
    }
</style>