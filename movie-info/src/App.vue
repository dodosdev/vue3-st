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
        <img :src="`${movie.imgUrl}`" :alt="movie.title"> 
        <!-- :src --이미지 경로를 동적으로 바꿔줌 (``)문자와변수를 같이작성가능 -->
      </figure>

      <!-- 영화 정보 -->
      <div class="info">
        <h3 class="bg-yellow" :style="movie.textRed">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button 
          @click="increaseLike(i)">좋아요
        </button>
        <span>{{ movie.like }}</span>
        <!-- 모달 열리는 버튼 -->
        <p>
          <button @click="isModal=true">상세보기</button>
        </p>
      </div>

      <!-- modal -->
      <div class="modal" v-if="isModal">
        <div class="inner">
          <h3>data[1]</h3>
          <p>영화 상세보기</p>
          <button @click="isModal=false">닫기</button>
        </div>
      </div>
    </div>
  </div>
</template>

<!--자바스크립트 변수나 데이터를 HTML에 꽂아넣는 데이터바인딩입니다.
그걸 {{데이터}} 이런 문법으로 HTML 중간중간에 쉽게 꽂아넣을 수 있습니다. -->


<script>
import data from "./assets/movies"; //data.js에서 데이터 가져오기
console.log(data);


export default {
  name: "App",
  data() {
    return {
      // isModal: false, //모달창 보이지 않는상태
      isModal: false, //모달창 보임
      movies: [
        {
          title: "미드",
          year: 2026,
          category: "액션",
          textRed: "color:black",
          like: 0,
          imgUrl:'./assets/jp-dorama.png',
        },
        {
          title: "노랑",
          year: 2023,
          category: "드라마, 액션",
          textRed: "color:black",
          like: 0,
          imgUrl:'./assets/mirai.jpeg',
        },
        {
          title: "드라마",
          year: 2024,
          category: "드라마, 판타지",
          textRed: "color:black",
          like: 0,
          imgUrl:'./assets/vini.jpeg',
        },
        {
          title: "일드",
          year: 2025,
          category: "힐링, 판타지",
          textRed: "color:black",
          like: 0,
          imgUrl:'./assets/jp-dorama.png',
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
/* .bg-yellow {
  padding: 10px;
} */

/* tab menu */
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

/* 영화 리스트 */
.movie {
  display: flex;
  justify-content: flex-start;
  margin-bottom: 20px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}
img{
  width: 200px;
  height: 300px;
}

button{
  margin-right: 10px;
  margin-top: 1rem;
}


/* 모달창 */
.modal{
  background: rgba(0, 0,0, 0.3);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner{
  background: white;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}

</style>
