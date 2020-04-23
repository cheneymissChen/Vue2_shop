<template>
    <div class="store-wrap">
        <header class="my-head">
            <i class="iconfont icon-left" @click="goBack"></i>
            <span>我的门店</span>
            <i class="iconfont icon-More"></i>
        </header>
      
        <section class="order-tag">
            <span :class="{'active' : orderType===1}" data-type="1" @click="selectTag">审批通过</span>
            <span :class="{'active' : orderType===2}" data-type="2" @click="selectTag">审批未通过</span>
            <span :class="{'active' : orderType===3}" data-type="3" @click="selectTag">审核中</span>
            <span :class="{'active' : orderType===4}" data-type="4" @click="selectTag">草稿箱</span>
        </section>
      <loading v-show="isLoading"></loading>
        <section>
            <div class="order-list" v-show="!isLoading">
                         <div class="order-item" v-for="(order,index) in orderList" :data-orderNo="order.orderNo" @click="viewDetail" :key="index" >
                    <p class="order-num">饰家小站上海1号店</p>
                    <div class="status">
                        <div>
                            <i>瑾哥哥</i>
                            <i>入驻时间：<b>2020-02-02</b></i>
                        </div>
                        <div>
                            <i>12345678901</i>
                            <i>签约金额：<b>30000.00</b></i>
                        </div>
                    </div>
                    <!-- <div class="product-list">
                        <div class="product-item" v-for="(product,index) in order.orderItemVoList" :key="index">

                            <img :src="order.imageHost+product.productImage" />
                            <div>
                                <p>{{product.productName}}</p>
                                <span>x{{product.quantity}}</span>
                            </div>
                        </div>
                    </div> -->
                </div>
            </div>
            <div class="order-empty" v-show="orderList.length === 0">{{emptyMsg}}</div>
        </section>

    </div>
</template>

<script>
    import loading from '../../components/common/loading'
    import {getUrlKey} from "../../common/js/util";
    import {orderList} from "../../service/getData";

    export default {
        data() {
            return {
                orderList: [], //所有订单
                orderType: 1,  //1-全部  2-待付款  3-待收货  4-已完成  5-售后
                emptyMsg: '',
                isLoading: true,
                
            }
        },
        created() {
            let $orderType = getUrlKey('orderType')
            this.orderType = parseInt($orderType)
            this.getOrderList()
         
        },
      mounted(){
          this.$nextTick(()=>{
            setTimeout(()=>{
              this.isLoading = false
            },500)
          })
      },
        methods: {
            getOrderList(){
                let pageNum = 1,
                    pageSize = 20
                orderList(pageSize,pageNum).then((res)=>{
                    console.log(res)
                 
                    this.initOrderList(res.data.list)
                })
            },
            initOrderList(orderList){
                switch(this.orderType){
                    case 1:
                        this.orderList = orderList
                        this.emptyMsg = '你的门店暂时没有审核通过!'
                        break
                    case 2:
                        orderList.forEach((order)=>{ 
                            if(order.status === 10){
                                this.orderList.push(order)
                            }
                        })
                        this.emptyMsg = '你的门店暂时没有审核未通过'
                        break
                    case 3:
                        this.orderList = []
                        this.emptyMsg = '你的门店没有审核中!'
                        break
                    case 4:
                        this.orderList = []
                        this.emptyMsg = '你的门店暂时没有草稿!'
                        break
                }
            },
            selectTag(e){
                let $type = parseInt(e.currentTarget.getAttribute('data-type'))
                this.orderType = $type
                this.orderList = []
                this.emptyMsg = ''
                this.getOrderList()
            },
            viewDetail(e){
                if(e.target.className === 'order-payment'){
                    return
                }
                this.$router.push('./order-detail?orderNo='+e.currentTarget.getAttribute('data-orderNo'))
            },
           
            goBack(){
                this.$router.push('./user')
            }
        },
        components: {
            loading
        }
    }
</script>

<style lang="scss" type="text/scss" scoped>
    @import '../../common/style/mixin';
    .store-wrap{
        background: #f7f7f7;
        .my-head{
            @include fj;
            width: 100%;
            height: 88px;
            padding: 0 20px;
            line-height: 88px;
            font-size: 30px;
            @include boxSizing;
            background: #fff;
            border-bottom: 1px solid #dcdcdc;
            .iconfont{
                font-size: 44px;
            }
        }
        .order-tag{
            display: flex;
            justify-content: space-around;
            width: 100%;
            background: #fff;
            span{
                height: 88px;
                line-height: 88px;
                font-size: 30px;
                &.active{
                    color: #00DBAC;
                    border-bottom: 6px solid #00DBAC;
                }
            }
        }
        .order-list{
            width: 100%;
         background: #f7f7f7;
            .order-item{
                   width: 90%;
                   box-sizing: border-box;
                   background: #fff;
                   margin: .4rem auto;
                .order-num{
                    padding: 20px 16px;
                    font-size: 30px;
                    color: #ffffff;
                    background:rgba(0,219,172,1);
                    border-radius:10px 10px 0px 0px;
                    span{
                        color: #000;
                    }
                }
                .status{
                    background: #ffffff;
                    @include fj;
                    @extend .order-num;
                    div{
                        display: flex;
                        flex-direction: column;
                        i{
                            font-style: normal;
                            padding-bottom: 10px;
                            color: #333333;
                            &:last-child{
                                b{
                                    font-weight: normal;
                                    color: #000;
                                  
                                }
                            }
                            b{
                                font-weight: normal;
                                color: $red;
                            }
                        }
                    }
                    span{
                        width: 154px;
                        height: 60px;
                        margin-top: 20px;
                        text-align: center;
                        line-height: 60px;
                        color: #fff;
                        background: $red;
                        @include borderRadius(10px);
                    }
                }
                .product-list{
                    width: 100%;
                    padding: 20px 0;
                    .product-item{
                        @include fj;
                        width: 100%;
                        margin-bottom: 20px;
                        img{
                            width: 150px;
                            height: 150px;
                        }
                        div{
                            width: 74%;
                            font-size: 28px;
                            span{
                                line-height: 60px;
                                color: #999;
                                font-size: 24px;
                            }
                        }
                    }
                }
            }
        }
        .order-empty{
            width: 100%;
          margin-top: 60px;
            text-align: center;
            font-size: 28px;
            color: #999;
        }
    }
</style>
