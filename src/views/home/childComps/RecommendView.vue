<template>
  <div class="recommend">
    <div v-for="(item,index) in recommends" :key="index" class="recommend-item">
      <a :href="item.link">
        <img :src="item.image" alt />
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    recommends: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>

<style scoped>
.recommend{
  width: 100%;
  display: flex;
  font-size: 12px;
  text-align: center;
  padding: 10px 0px 20px 0px;
  border-bottom: 10px solid #eee;
}

.recommend-item{
  flex: 1;
}
.recommend-item img{
  width: 90%;
  margin-bottom: 10px;
}
</style>
