<template>
<!-- modal component-->
<div class="modal" v-if="isModal">
  <div class="inner">
    <h3>{{ data[selectedMovie].title }}</h3>
    <p>영화 상세정보</p>

    <!-- 모달창 닫기 버튼 -->
    <!--자식컴포넌트가 부모에게 데이터 변경을 요청할수 있음-->
    <!-- <button @click="isModal = false">닫기</button> -->
    <button @click="$emit('closeModal')">닫기</button>
    <!--클릭했을때 isModal이라는 상태변수를 변경해야하는데 isModal변수는 App.vue에 있어서 Modal.vue컴포넌트에 전달해야함 (props 이용)-->
    
  </div>
</div>
</template>

<script>
export default {
  name: "ModalComponent", //이름이 ModalComponent인 컴포넌트
  props: { //전달받은 상태변수들을 등록
    data: Array, //부모에서 보낸 props변수
    isModal: Boolean,
    selectedMovie: Number,
  }
}

</script>

<style>
  .modal .inner{
  background: white;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>