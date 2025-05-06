<template>
  <div class="event">
    <p>{{ text }}</p> 
  </div>
</template>


<script>
  export default {
    name: "EventComponent", //이름이 EventComponent인 컴포넌트
    props:{
      text:String, //변수명: 자료형 //부모에서 보낸 props변수
    }
  }

</script>


<style>
  .event{
    background: #666;
    color: #fff;
    padding: 10px 20px;
    text-align: center;
    font-size: small;
  }

  .event p {
    margin: 0;
  }
</style>