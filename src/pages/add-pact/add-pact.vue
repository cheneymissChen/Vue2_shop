<template>
  <div class="addpact-box">
    <header class="user-head">
      <i class="iconfont icon-left" @click="goBack"></i>
      <span style="font-size:34px;font-weight:bold;height:110px;line-height:110px;">添加合同</span>
      <i class="iconfont icon-More" ></i>
    </header>
    <section>
      <div class="addpact-list">
        <div class="item">
          <span class="store-info">门店基础信息(必填)</span>
        </div>
        <div class="item">
          <label for="store-name">门店名称:</label>
          <input type="text" id="store-name" placeholder="请输入门店名称" />
        </div>
        <div class="item">
          <label for="contacts">联系人:</label>
          <input type="text" id="contacts" placeholder="请输入联系人" />
        </div>
        <div class="item">
          <label for="contacts-way">联系方式:</label>
          <input type="text" id="contacts-way" placeholder="请输入联系方式" />
        </div>
        <div class="item">
          <van-field
            readonly
            clickable
            label="门店地址:"
            :value="value"
            placeholder="选择城市"
            @click="showPicker = true"
          />
          <van-popup v-model="showPicker" position="bottom">
            <van-picker
              show-toolbar
              title="请选择地址"
              :columns="columns"
              @cancel="showPicker = false"
              @confirm="onConfirm"
            />
          </van-popup>
        </div>
        <div class="item">
          <label for="detailed-address">详细地址:</label>
          <input type="text" id="detailed-address" placeholder="请输入详细地址" />
        </div>
        <div class="item">
          <label for="business-license">营业执照:</label>
          <div class="business-license image">
            <van-uploader v-model="fileLists" multiple :max-count="1" preview-size="350px"  image-fit="cover"/>
            
          </div>
        </div>
      </div>
        <div class="addpact-list">
        <div class="item">
          <span class="store-info">收款信息(二选一必填)</span>
        </div>
        <div class="item" style="border:none;">
          <label for="contract-amount">合同金额:</label>
          <input type="text" id="contract-amount" placeholder="请输入合同金额" />
        </div>
        <div class="item">
          <label for="store-paid">门店已付款:</label>
          <div class="store-paid image">
             <van-uploader v-model="fileLi" multiple :max-count="1" preview-size="360px"  image-fit="cover"/>
          </div>
        </div>
        <div class="item" style="border:none;">
          <label for="contract-photos">合同照片:</label>
          <div class="contract-photos">
            <van-uploader v-model="fileList" multiple preview-size="160px" style="float:left;margin-left：10px; border: 3px #ededed solid;"/>
           
          </div>
        </div>
        </div>
         <div class="addpact-list">
        <div class="item">
          <span class="store-info">补充信息(可不填)</span>
        </div>
        <div class="item" style="border:none;">
          <label for="logo">门店LOGO:</label>
          <div class="logo-img image" style="margin-bottom:160px;" >
              <van-uploader v-model="fileLis" multiple :max-count="1" preview-size="360px"  image-fit="cover"/>
               
          </div>
        </div>
      </div>
       
    </section>
    <footer>
      <div class="footer">
        <button class="save">保存到草稿箱</button>
        <button class="commit" @click="oncommit">提交</button>
      </div>
    </footer>
  </div>
  
</template>

<script>
import { Toast } from 'vant';
export default {
  data() {
    return {
      imgDatas: [],
      value: "",
      showPicker: false,
          fileList: [],
      fileLists:[],
      fileLis:[],
       fileLi:[],
      // columns: ['杭州', '宁波', '温州', '嘉兴', '湖州'],
      columns: [
        {
          text: "浙江",
          children: [
            {
              text: "杭州",
              children: [{ text: "西湖区" }, { text: "余杭区" }]
            },
            {
              text: "宁波",
              children: [{ text: "江东区" }, { text: "鄞州区" }]
            }
          ]
        },
        {
          text: "安徽",
          children: [
            {
              text: "合肥",
              children: [{ text: "滨湖区" }, { text: "政务区" }]
            },
            {
              text: "安庆",
              children: [{ text: "秀山区" }, { text: "怀宁县" }]
            }
          ]
        }
      ]
    };
  },
  methods: {
    onConfirm(value) {
      let str = value.join(",");
      console.log(str);
      this.value = str;
      this.showPicker = false;
    },
    oncommit(){
      alert("书写提交代码逻辑")
    },
    goBack() {
      this.$router.go(-1);
    }
  },
  components: {}
};
</script>

<style lang="scss"  type="text/scss" scoped>
@import "../../common/style/mixin";

   
.addpact-box {
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
  section{
    background: #f7f7f7;
  }
  
  .addpact-list {
    width: 90%;
    display: flex;
    flex-direction: column;
    margin: 30px auto;
    background: #ffffff;
    .item {
      padding: 0 20px;
      line-height: 88px;
      font-size: 34px;
      margin-bottom: 20px;
      box-sizing: border-box;
      border-bottom:3px #ededed dashed;
   
      .store-info {
        display: flex;
        color: #00dbac;
        font-size: 42px;
        font-weight: bold;
      }
      
      /deep/ .van-cell {
        position: relative;
        display: -webkit-box;
        display: -webkit-flex;
        display: flex;
        box-sizing: border-box;
        width: 100%;
        padding: 0;
        overflow: hidden;
        color: #333;
        font-size: 36px;
        line-height: 88px;
      }
      /deep/ .van-picker__toolbar {
        line-height: 88px;
        height: 88px;
      }
      /deep/ .van-picker-column {
        font-size: 36px;
      }
      /deep/ .van-picker__columns {
        height: 450px !important;
      }
      /deep/ .van-picker-column ul {
        line-height: 0 !important;
        height: 0 !important;
      }
      /deep/ .van-picker-column ul li {
        line-height: 88px !important;
        height: 88px !important;
        color: #999;
      }
      /deep/ .van-popup button {
        font-size: 40px !important;
      }
      /deep/ .van-field__label {
        font-size: 36px;
        display: inline-block;
        width: 210px;
        text-align: justify;
        text-align-last: justify;
        color: #333;
        text-indent: 0;
        padding-left: 0;
      }
      /deep/ .van-field__control {
        text-indent: 30px;
      }
      /deep/ .van-picker__title {
        font-size: 36px;
        color: #333;
      }
       /deep/ .van-uploader__preview-image {
    display: block;
    width: 1.066667rem;
    height: 1.066667rem;
    overflow: hidden;
    border-radius: 0.106667rem;
    margin-left: 30px;
}
/deep/ .van-uploader__upload-icon {
    color: #dcdee0;
    font-size: 60px;
}
/deep/ .van-uploader__upload {
    position: relative;
    display: -webkit-box;
    display: -webkit-flex;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -webkit-flex-direction: column;
    flex-direction: column;
    -webkit-box-align: center;
    -webkit-align-items: center;
    align-items: center;
    -webkit-box-pack: center;
    -webkit-justify-content: center;
    justify-content: center;
    box-sizing: border-box;
    width: 1.066667rem;
    height: 1.066667rem;
    margin: 0 0.106667rem 0.106667rem 0;
    border-radius: 0.106667rem;
    background:#ffffff;
   
}
      label {
        font-size: 36px;
        display: inline-block;
        text-align: justify;
        text-align-last: justify;
        color: #333333;
      }
     
      input {
        width: 300px;
        text-indent: 20px;
        color: #c4c4c5;
      }
      .image {
        height: 360px;
        line-height: 360px;
        text-align: center;
        border: 3px #ededed dashed;
        margin: 0 auto;
        color: #00DBAC;
        font-weight: bold;
        position: relative;
        img {
          width: 100%;
          height: 100%;
          vertical-align: top;
          
        }
      }
    
      
      .contract-photos {
        position: relative;
        // width: 30%;
        height: 160px;
        text-align: center;
        margin: 20px 0px;
        img {
          width: 100%;
          height: 100%;
          vertical-align: top;
        }
      }
    
    }
  }
  .footer {
    width: 90vw;
    height: 88px;
    display: flex;
    font-size: 40px;
    line-height: 88px;
    margin: 50px auto;
    text-align: center;
    position: fixed;
    left: 6%;
    bottom: 0%;
    background: #f7f7f7;
    border-top: 30px #f7f7f7 solid;
    .save {
      flex: 1;
      background: #999;
      color: #fff;
      margin: 0 10px;
    }
    .commit {
      flex: 1;
      background: #00dbac;
      color: #fff;
      margin: 0 30px;
    }
  }
}

 
</style>
