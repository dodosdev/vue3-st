<template>
  <h1>{{영화 정보}}</h1>  
  <p>영화제목 1</p>
  <p>개봉: 2023</p>
  <p>장르 : 액션</p>
</template>
ㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴㄴ


<script>
//데이터 작성 기능들 정의
export default {
  name: 'App',
  data() {   
    return{  //상태변수(state value)화면에 자주 업데이트 되는 변수들을 정의함 a'return'을 통해서
      title:"노랑",
      year: 2025,
      category: "액션, 드라마"

    }
  }
}

</script>

<style>

</style>
