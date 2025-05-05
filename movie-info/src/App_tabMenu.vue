<template>
  <h1>영화 정보</h1>  
  <div v-for="(movie, i) in data" :key="i">
    <h3 class="bg-yellow" :style="textRed">{{movie.title}}</h3> 
    <!--:style="texsRed">  :속성명="데이터"-->
    <p>개봉: {{  movie.year }}</p>
    <!-- <p>장르 : {{  data[i].category }}</p> -->
    <p>장르 : {{  movie.category }}</p>
    <!-- <button @:click="like++">좋아요</button><span>{{ movie.like }}</span> -->
    <button 
      @:click="increseLike(i)">좋아요
    </button><span>{{ movie.like }}</span>
    <!-- v-on:이벤트명="실행코드" -->

  </div>
  <!-- <p v-for="(item, i) in foods" :key="i">{{ item }}</p>  -->
  <!--// :key="i">  :key="키값" 배열번호 자료를 구분할수 있는 고유번호가(키값)  반드시 필요함!!-->
  <!-- 데이터가 변경이되면 자료가 업데이트됨 반복문을 사용시 각각의 키값이 필요함!! -->
  <div>
        <!-- 탭 버튼 -->
    <div class="tab-buttons">
      <button 
        v-for="(tab, index) in tabs" 
        :key="index"
        @click="currentTab = index"
        :class="{ active: currentTab === index }"
      >
        {{ tab.name }}
      </button>
    </div>

    <!-- 탭 콘텐츠 -->
    <div class="tab-content">
      <component :is="tabs[currentTab].component" />
    </div>
  </div>
</template>
    <!-- v-for 디렉티브를 사용하여 반복문을 사용하여 화면에 표시함
    v-for="아이템명 in array" 아이템명은 array가 반복되면서 불러올 요소 하나하나를 의미함. n array는 실제적으로 반복을 할 데이터 묶음을 넣어주면 됨
    <div id="app">
      <h1>장 볼 리스트</h1>
      <ul>
        <li v-for="item in list">{{ item }}</li>
      </ul>
    </div> -->



<script>

//데이터 작성 기능들 정의
export default {  
  name: 'App', 
  data() {    //data()데이터를 정의하는 함수ß
    return{  //상태변수(state value)화면에 자주 업데이트 되는 변수들을 정의함 a'return'안에 문서에 표시될 변수 정의

      data:[
        {
          title:"미드",
          year:2026,
          category:"액션, 판타지, 어드벤처",
          textRed:"color:red",
          like:0, //변수 추가
        },
        {
          title:"노랑",
          year:2023,
          category:"액션, 판타지, 어드벤처",
          textRed:"color:red",
          like:0, //변수 추가
        },
        {
          title:"드라마",
          year:2024,
          category:"액션, 판타지, 어드벤처",
          textRed:"color:red",
          like:0, 
        },
        {
          title:"일드",
          year:2025,
          category:"액션",
          textRed:"color:orange",
          like:0, 
        }
      ]
        
    }
  },
  methods: {
    increseLike(i) {
      this.data[i].like += 1;
    }
  }
}
</script>




<style>
  .bg-yellow{
    background-color: gold;
    padding: 10px;
  }
</style>



