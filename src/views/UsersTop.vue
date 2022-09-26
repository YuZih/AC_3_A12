<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <div class="col-3">
        <a href="#">
          <img
            src="貼上引用圖片網址，同學可自行選擇圖片進行實作"
            width="140px"
            height="140px"
          />
        </a>
        <h2>User</h2>
        <span class="badge badge-secondary">追蹤人數：3</span>
        <p class="mt-3">
          <button type="button" class="btn btn-danger">取消追蹤</button>
          <button type="button" class="btn btn-primary">追蹤</button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
export default {
  components: {
    NavTabs,
  },
};
</script>