<template>
  <div id="detail_comment" v-if="Object.keys(comment).length != 0">
    <div class="comment_title">
      <span class="comment_name">用户评价</span>
      <span class="comment_more">更多</span>
    </div>
    <div class="comment_info">
      <div class="u_info">
        <img :src="comment.user.avatar" alt />
        <span>{{ comment.user.uname }}</span>
      </div>
      <div class="comment_content">
        <div class="content">{{ comment.content }}</div>
        <p class="content_info">{{ comment.created | dateShow }} {{ comment.style }}</p>
      </div>
    </div>
    <div class="shop_reply" v-if="comment.explain != null">{{ comment.explain }}</div>
    <div class="comment_img" v-if="comment.images != null">
      <img :src="item" alt v-for="(item, index) in comment.images" :key="index" />
    </div>
  </div>
</template>
<script>
import { formatDate } from "common/utils.js";
export default {
  props: {
    comment: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  filters: {
    dateShow(value) {
      let date = new Date(value * 1000);
      return formatDate(date, "yyyy-MM-dd");
    },
  },
};
</script>
<style scoped>
#detail_comment {
  padding: 0 10px;
  font-size: 14px;
  padding-bottom: 10px;
  border-bottom: 5px solid #f2f5f8;
  margin-bottom: 10px;
}
.comment_title {
  width: 100%;
  margin-bottom: 7px;
  line-height: 44px;
  border-bottom: 2px solid #f7f5f7;
}
.comment_title .comment_more {
  float: right;
  /* margin-right: 10px; */
}
.comment_info {
  position: relative;
  width: 100%;
}

.comment_info .u_info img {
  border-radius: 50%;
  width: 30px;
  height: 30px;
  margin-right: 3px;
}
.comment_info .u_info span {
  position: absolute;
  top: 8px;
}
.content {
  line-height: 20px;
  color: #888888;
}
.content_info {
  margin: 5px 0;
  color: #888888;
}
.comment_img {
  width: 100%;
  display: flex;
}
.comment_img img {
  margin-right: 2px;
  width: 100px;
  height: 100px;
}
</style>
