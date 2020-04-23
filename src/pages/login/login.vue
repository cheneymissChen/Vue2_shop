<template>
    <div>
        <img src="../../assets/login_bg.png" class="login">
        <div class="register" @click="handrefister">注册</div>
        <section class="page">
            <div class="login-page">
                <div class="login-wrap">
                    <div class="login-text">
                        <input @mouseenter="focusText"
                               @mouseleave="blurText" v-model="username" type="text" class="login-username" placeholder="用户名/邮箱/已验证手机" />
                        <i class="iconfont icon-close" data-close="username" v-show="!usernameClose" @click="clearText"></i>
                    </div>
                    <div class="login-text">
                        <input @mouseenter="focusText"
                               @mouseleave="blurText" ref="passwordText" v-model="password" type="password" class="login-password" placeholder="请输入密码"  />
                        <div>
                            <i class="iconfont icon-close" data-close="password" v-show="!passwordClose" @click="clearText"></i>
                            <i class="iconfont icon-eye1 eye" @click="changeType" v-if="!passwordType" ></i>
                            <i class="iconfont icon-eye eye" @click="changeType" v-else></i>
                            <!-- <router-link tag="span" to="./forget-password">忘记密码</router-link> -->
                        </div>
                    </div>
                </div>
                <div class="login-error">{{errMsg}}</div>
                <button class="login-button" :class="{'active' : removeSpace(username)&&removeSpace(password)}" @click="loginSubmit">登  录</button>
                <div class="quick-nav">
                    <!-- <router-link tag="span" class="register-button" to="./register">快速注册</router-link> -->
                </div>
                 <div class="other-login">
                    <div class="other-head">
                        <i></i>
                        <span>第三方账号登录</span>
                        <i></i>
                    </div> 
                    <div class="other-con">
                        
                        <div class="login-icon">
                                <img src="../../assets/wechat.png" class="wechat">
                        </div>
                    </div> 
                   
                </div> 
            </div>
        </section>
     
    </div>
</template>

<script>
    // import mHeader from 'components/common/m-header'
    import popup from 'components/common/popup'
    import {removeSpace} from "../../common/js/util";
    import {userLogin} from '../../service/getData'

    export default {
        data() {
            return {
                username: '',
                password: '',
                errMsg: '',
                usernameClose: true,
                passwordClose: true,
                passwordType: 0
            }
        },
        methods: {
            focusText(e){
                let $className = e.currentTarget.className
                $className === 'login-username' ? this.usernameClose = false : this.passwordClose = false
            },
            blurText(e){
                let $className = e.currentTarget.className
                $className === 'login-username' ? this.usernameClose = true : this.passwordClose = true
            },
            clearText(e){
                let $close = e.currentTarget.getAttribute('data-close')
                console.log($close)
                this[$close] = ''
            },
            changeType(){
                let $type = this.$refs.passwordText.getAttribute('type'),
                    value = ''
                console.log($type)
                $type === 'password' ? value = 'text' : value = 'password'
                this.$refs.passwordText.setAttribute('type',value)
                this.passwordType = !this.passwordType
            },
            removeSpace(value){
                return removeSpace(value)
            },
            loginSubmit(){
                if(!this.username || !this.password){
                    return
                }
                userLogin(this.username,this.password).then((res)=>{
                        this.errMsg = ''
                        this.$router.push('./center')
                })
            },
            //点击注册跳转到注册页面
            handrefister(){
              this.$router.push("./register")
            }
        },
        components: {
            // mHeader,
            popup
        }
    }
</script>

<style lang="scss" type="text/scss" scoped>
    @import '../../common/style/mixin';
    .login{
          width: auto;  
          height: auto;  
         max-width: 100%;  
         max-height: 100%; 
         position: relative;
        
    }
     .register{
            position:absolute;
            top:60px;
            right: 60px;
            color: #ffffff;
            font-size:30px;
            font-weight: bold;
            font-family:PingFang SC;
         }

    .login-page{
     
        margin-top: 60px;
        .login-wrap{
            width: 100%;
            .iphone{
                width: 6%;
                height: 40px;
                margin: 2% 4%;
            }
             .code{
                width: 6%;
                height: 40px;
                margin: 2% 4%;
            }
            .login-text{
                @include fj;
                width: 90%;
                margin: 0 auto;
                height: 60px;
                line-height: 60px;
                padding: 20px 0;
                margin-top: 20px;
                border-bottom: 1px solid #dcdcdc;
                .iconfont{
                    font-size: 26px;
                    color: #CCCCCC;
                    &.eye{
                        padding: 0 30px;
                        font-size: 40px;
                       
                    }
                }
                input{
                    width: 100%;
                    height: 100%;
                    margin-right: 20px;
                    line-height: 60px;
                    color: #222;
                    font-size: 32px;
                    &.login-password{
                        width: 50%;
                    }
                }
                span{
                    // padding-left: 20px;
                    font-size: 30px;
                  
                }
                div{
                    display: flex;
                }
            }
        }
        .login-error{
            width: 100%;
            height: 40px;
            line-height: 40px;
            padding: 30px 0;
            color: $red;
            font-size: 26px;
        }
        .login-button{
            width: 100%;
            height: 100px;
            text-align: center;
            line-height: 100px;
            color: #fff;
            font-size: 32px;
            background:rgba(255,157,17,1);
             border-radius:36px;
            @include borderRadius(60px);
            &.active{
              background:rgba(255,157,17,1);
            }
        }
        .quick-nav{
            padding: 40px 0;
            width: 100%;
            text-align: right;
            .register-button{
                color: #999;
                font-size: 28px;
            }
        }
        .other-login{
            width: 100%;
            .other-head{
                @include fj;
                i{
                    flex: 1;
                    height: 1px;
                    margin-top: 18px;
                    background: #dcdcdc;
                }
                span{
                    flex: 1;
                    text-align: center;
                    font-size: 28px;
                    color: #dcdcdc;
                }
            }
            .other-con{
                display: flex;
                width: 320px;
                padding: 40px 0;
                margin: 0 auto;
                .login-icon{
                    display: flex;
                    flex-direction: column;
                    width: 96px;
                    margin: 0 auto;
                    text-align: center;
                    .iconfont{
                        width: 100%;
                        height: 96px;
                        line-height: 96px;
                        font-size: 60px;
                        color: #15B8F5;
                        background: #E7F7FE;
                        @include borderRadius(50%);
                        &.icon-weixin1{
                            font-size: 50px;
                            color: #09BB07;
                            background: #E6F8E6;
                        }
                    }
                   
                }
            }
         
        }
    }
    .wechat{
        width: 80px;
        height: 80px;
        border-radius: 50%;
    }
   
  
</style>
