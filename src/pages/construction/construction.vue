<template>
    <div class="construction_container">
   <div class="pay_succes_wrap"  >
    <div class="img_icion">
        
        <img src="../../assets/construction.png" class="img_icion">

    </div>
    <div class="construction_title">功能建设中，敬请期待！</div>

    <div class="affirm ">确定</div>

</div>


    </div>
</template>
<script>
export default {
    data(){
        return{

        }
      
    },
    methods: { 
        goBack(){
            this.$router.go(-1);
        }
        },
}
</script>
<style lang="scss" scoped>
@import "../../common/style/mixin";
.construction_container {
  background: #ffffff;
  .pay_succes_wrap{
	margin: auto;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	margin-top: 35%;
	
	
	.img_icion{
        width: 400px;
        height: 350px;
	}
	
	.construction_title{
		
		height: 80px;
		line-height: 80px;
		text-align: center;
		font-size: 38px;
        color: #333333;
        font-family: PingFangSC-Regular;
        margin-top: 40px;
	}
	
   
   .affirm {
    // width: 90%;
    width: 583px;
    height: 100px;
    line-height: 100px;
    text-align: center;
    background: #00DBAC;
    border-radius: 47px;
    color: #fff;
    font-size: 36px;
    font-weight: bold;
    margin: 60px auto;
   	
   	
   }
   }
}
</style>