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
          <p>
            <a href="/users/2/edit"
              ><button type="submit" class="btn btn-primary">edit</button></a
            >
          </p>
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
  },
  data() {
    return {
      currentUser: {
        // id: 1;
        name: "root",
        email: "root@example.com",
        // password: "$2a$10$OJ3jR93XlEMrQtYMWOIQh.EINWgaRFTXkd0Xi5OC/Vz4maztUXEPe";
        // isAdmin: true;
        // image: "https://i.imgur.com/58ImzMM.png";
        // createdAt: "2019-07-30T16:24:54.983Z";
        // updatedAt: "2019-08-01T10:33:51.095Z";
      },
      userComments: [],
      userFavoritedRestaurants: [],
      userFollowers: [],
      userFollowings: [],
    };
  },
  created() {},
  methods: {},
};
</script>
