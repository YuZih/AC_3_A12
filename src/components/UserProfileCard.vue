<template>
  <div class="card mb-3">
    <div class="row no-gutters">
      <div class="col-md-4">
        <img :src="profile.image" width="300px" height="300px" />
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ profile.name }}</h5>
          <p class="card-text">{{ profile.email }}</p>
          <ul class="list-unstyled list-inline">
            <li>
              <strong>{{ commentNum }}</strong> 已評論餐廳
            </li>
            <li>
              <strong>{{ favoriteNum }}</strong> 收藏的餐廳
            </li>
            <li>
              <strong>{{ followerNum }}</strong> followings (追蹤者)
            </li>
            <li>
              <strong>{{ followingNum }}</strong> followers (追隨者)
            </li>
          </ul>
          <template v-if="isCurrentUser">
            <router-link
              :to="{ name: 'user-edit', params: { id: profile.id } }"
              class="btn btn-primary"
            >
              Edit
            </router-link>
          </template>
          <template v-else>
            <button
              v-if="isFollowed"
              type="button"
              class="btn btn-danger"
              @click.stop.prevent="deleteFollowing()"
            >
              取消追蹤
            </button>
            <button
              v-else
              type="button"
              class="btn btn-primary"
              @click.stop.prevent="addFollowing()"
            >
              追蹤
            </button>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    profile: {
      type: Object,
      required: true,
    },
    commentNum: {
      type: Number,
      required: true,
    },
    favoriteNum: {
      type: Number,
      required: true,
    },
    followerNum: {
      type: Number,
      required: true,
    },
    followingNum: {
      type: Number,
      required: true,
    },
    isCurrentUser: {
      type: Boolean,
      required: true,
    },
    initialIsFollowed: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      isFollowed: this.initialIsFollowed,
    };
  },
  created() {},
  methods: {
    addFollowing() {
      this.isFollowed = true;
    },

    deleteFollowing() {
      this.isFollowed = false;
    },
  },
};
</script>
