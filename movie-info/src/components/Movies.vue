<template>
  <div class="container">
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

    <!-- tab메뉴 장르별 보여주는 필터 -->
    <div v-for="(movie, i) in filteredMovies" :key="i" class="movie">
    
    
      <figure>
        <!-- :src --이미지 경로를 동적으로 바꿔줌 (``)문자와변수를 같이작성가능 -->
        <img :src="`${movie.imgUrl}`" :alt="movie.title"> 
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
          <button @click="isModal=true; selectedMovie=i">상세보기</button>
        </p>
      </div>
    </div>

  </div>
</template>


<script>
  export default { //컴포넌트 내보내기
    name: "MoviesComponent", //이름이 MoviesComponent인 컴포넌트
    props: {
      data: Array, //부모에서 보낸 props변수

    }
  }

</script>


<style>
  .container {
    padding: 20px;
  }
</style>