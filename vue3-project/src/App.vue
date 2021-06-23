// 컴포넌트는 하나의 부품 ~ 컴포넌트 만들때 확장자 .vue 로 들어감 

//templat 안에 div 들어감
<template>
  <!-- <div class="name">{{ name }}</div> -->
  <div class="name">{{ great }}</div>

</template>

// 자바스크립트 작성
<script>
export default {
  setup() {
    const name = 'hussey Kim';

    const greeting = (name) => {
      return 'Hello ' + name;
    };

    const great = greeting(name);

    //원하는 변수 리턴을 해줘야 template 에서 접근이 가능해짐 
    return {
      great
    };
  }
  
}
</script>


//css 코드
<style>
  .name {
    color : blue;
  }

</style>
