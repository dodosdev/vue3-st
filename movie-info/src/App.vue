<template>
  <div>
    <h1>영화 정보</h1>

    <!-- 탭 버튼 -->
    <div class="tabs">
      <button
        v-for="(genre, index) in genreTabs"
        :key="index"
        :class="{ active: currentTab === genre }"
        @click="currentTab = genre"
      >
        {{ genre }}
      </button>
    </div>

    <!-- 영화 리스트 -->
    <div v-for="(movie, i) in filteredMovies" :key="i" class="movie">
      <figure>
      </figure>
      <h3 class="bg-yellow" :style="movie.textRed">{{ movie.title }}</h3>
      <p>개봉: {{ movie.year }}</p>
      <p>장르: {{ movie.category }}</p>
      <button @click="increaseLike(i)">좋아요</button>
      <span>{{ movie.like }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      movies: [
        {
          title: "미드",
          year: 2026,
          category: "액션",
          textRed: "color:red",
          like: 0,
        },
        {
          title: "노랑",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          textRed: "color:red",
          like: 0,
        },
        {
          title: "드라마",
          year: 2024,
          category: "드라마, 힐링",
          textRed: "color:red",
          like: 0,
        },
        {
          title: "일드",
          year: 2025,
          category: "힐링, 판타지",
          textRed: "color:orange",
          like: 0,
        },
      ],
      genreTabs: ["전체", "액션", "드라마", "판타지"], //장르 탭
      currentTab: "전체",
    };
  },
  computed: {
    filteredMovies() { //선택된 탭에 따라 filteredMovies에서 자동 필터링
      if (this.currentTab === "전체") return this.movies;
      return this.movies.filter((movie) =>
        movie.category.includes(this.currentTab)
      );
    },
  },
  methods: {
    increaseLike(i) { //좋아요 버튼 클릭 시 like 수 증가
      this.movies[i].like += 1; //객체 안에있는 변수를 찾아야하기 때문에 this를 사용
    },
  },
};
</script>

<style scoped>
.bg-yellow {
  background-color: gold;
  padding: 10px;
}

.tabs {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
.tabs button {
  padding: 8px 16px;
  border: 1px solid #ccc;
  background: #eee;
  cursor: pointer;
}
.tabs button.active {
  background: #222;
  color: white;
}
.movie {
  margin-bottom: 20px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}
</style>
