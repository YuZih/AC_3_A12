// ./src/views/Restaurants.vue
<template>
  <div class="container py-5">
    <!-- 使用 NavTabs 元件 -->
    <NavTabs />

    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />
    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import RestaurantCard from "../components/RestaurantCard.vue";
import RestaurantsNavPills from "../components/RestaurantsNavPills.vue";
import RestaurantsPagination from "../components/RestaurantsPagination.vue";
//建立種子資料
const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Stephany Hintz",
      tel: "520-873-2784",
      address: "302 Emery Brook",
      opening_hours: "08:00",
      description: "illum",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=44.90453477594259",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: "Ms. Abdiel Hermann",
      tel: "(163) 482-9125",
      address: "1325 Betty Lane",
      opening_hours: "08:00",
      description: "Et labore id provident maiores atque voluptas quam",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=52.983595343391784",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: "Zaria Donnelly",
      tel: "(599) 820-3815 x6051",
      address: "7483 Sammie Avenue",
      opening_hours: "08:00",
      description: "Sunt molestiae quis. Itaque maiores sint quos et q",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=81.48600139258212",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Jermey Langosh",
      tel: "946.003.1797 x7271",
      address: "719 Thompson Circles",
      opening_hours: "08:00",
      description: "At excepturi vel sint dignissimos libero velit imp",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=42.7175880095876",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Everette Cormier",
      tel: "1-848-530-8493",
      address: "925 Bosco Freeway",
      opening_hours: "08:00",
      description: "Aperiam ut qui incidunt corrupti repellat. Impedit",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=11.653044204898922",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: "Elise Wehner",
      tel: "873-667-1048",
      address: "931 Douglas Freeway",
      opening_hours: "08:00",
      description: "Repudiandae vero facere. Quae labore dolorum volup",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=74.52335962078114",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Miss Sebastian Steuber",
      tel: "(190) 097-8402",
      address: "0985 Gardner Underpass",
      opening_hours: "08:00",
      description: "neque",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=35.45257544254861",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: "German Blanda",
      tel: "1-665-334-5287",
      address: "3125 Michele Island",
      opening_hours: "08:00",
      description: "Ea praesentium et. Fugit qui qui. Et iure blanditi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=75.04113229854623",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Dulce Braun",
      tel: "(351) 697-5124",
      address: "064 Weissnat Harbor",
      opening_hours: "08:00",
      description: "Optio porro quisquam dolorem debitis voluptatum id",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=3.5940946354535264",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Mikayla Wiza",
      tel: "870-294-7664",
      address: "4432 Zora Highway",
      opening_hours: "08:00",
      description: "quia",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=69.64006464968378",
      viewCounts: 0,
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-09-24T16:11:54.000Z",
        updatedAt: "2022-09-24T16:11:54.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-09-24T16:11:54.000Z",
      updatedAt: "2022-09-24T16:11:54.000Z",
    },
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  name: "Restaurants",
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [], //影片教案原本寫-1
      previousPage: -1,
      nextPage: -1,
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    },
  },
};
</script>
