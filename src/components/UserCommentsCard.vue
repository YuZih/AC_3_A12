<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ commentNum }}</strong> 已評論餐廳
    </div>
    <div class="card-body">
      <router-link
        v-for="comment in comments"
        :key="comment.id"
        :to="{ name: 'restaurants', query: { commentId: comment.id } }"
      >
        <img
          :src="comment.Restaurant.image"
          width="60"
          height="60"
          class="avatar"
        />
      </router-link>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    comments: {
      type: Array,
      require: true,
    },
  },
  data() {
    return {
      commentNum: this.comments.length,
    };
  },
};
</script>
