<template>
    <nav class="navbar">
      <a href="#">Home</a>
      <a href="#">Movies</a>
      <a href="#">About</a>
    </nav>
</template>


<script>
  export default {  //컴포넌트 내보내기
    name: 'NavbarComponent', //이름이 NavbarComponent인 컴포넌트
  }

</script>


<style>
.navbar {
  background: #000;
  padding: 20px;
  text-align: center;
}
  
.navbar a {
  color: #fff;
  text-decoration: none;
  padding: 1em;
}
</style>