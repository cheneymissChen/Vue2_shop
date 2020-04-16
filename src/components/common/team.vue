<template>
  <div>
    <!-- 团队业绩 -->
    <div class="team_container">
      <div class="earn_wrap">
        <div class="earn_item">
          <img src="../../assets/team_members.png" class="incon_img" />
          <div class="contract_title">团队成员</div>
        </div>
        <div class="earn_item">
          <img src="../../assets/team_performance.png" class="incon_img" />
          <div class="contract_title">团队绩效</div>
        </div>
      </div>
      <div class="earn_wrap">
        <div class="earn_item">
          <img src="../../assets/group_stores.png" class="incon_img" />
          <div class="contract_title">团队门店</div>
        </div>
        <div class="earn_item">
          <img src="../../assets/team_rank.png" class="incon_img" />
          <div class="contract_title">团队排名</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
  methods: {}
};
</script>

<style lang="scss" type="text/scss" scoped>
@import "../../common/style/mixin";
.team_container {
  width: 100%;
  height: 400px;
  display: flex;
  flex-direction: column;
  margin: 40px auto;
}
.earn_wrap {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  text-align: center;
}
.earn_item {
  width: 48%;
  height: 240px;
  background: #ffffff;
  margin-bottom: 30px;
}
.incon_img {
  width: 100px;
  height: 100px;
  padding: 20px 54px 20px 54px;
}
.contract_title {
  height: 60px;
  line-height: 60px;
  text-align: center;
  font-size: 36px;
  font-weight: bold;
}
.nav_list {
  margin: 0px;
}
</style>
