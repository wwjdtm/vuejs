// 컴포넌트는 하나의 부품 ~ 컴포넌트 만들때 확장자 .vue 로 들어감 

//templat 안에 div 들어감
<template>
  <!-- <div class="name">{{ name }}</div> -->
  
  <!-- <div >{{ name2.id }}</div> -->

  <!-- 바인딩 하는방법. -> 인풋에 name 데이터 넣어줌 -->
  <!-- input 의 속성 : type, value -- 모두 v-bind 가능 / v-bind 생략가능-->

  <!-- v-model: value 양방형  바인딩 + 업데이트 한번에 해줌 -->
  <input type="text" v-model="name">
  
  <!-- v-on -> @ 생략가능 -->
  <button 
    class = "btn btn-primary" @click="onsubmit">  Click </button>

</template>

// 자바스크립트 작성
<script>
// 함수에서 변수값을 변경시켰을때 html 에도 적용이 되도록 하기위해 ref 임포트 , ref로 선언하고, 변수.value로 접근
import { ref } from 'vue';
//object 나 array 일때는 reactive 를 임포트함
import { reactive } from 'vue';

export default {
  setup() {
    const name = ref('hussey Kim');
    const name2 = reactive({
      id : 2343
    });

    // const greeting = (name) => {
    //   return 'Hello ' + name;
    // };
    const onsubmit = () => {
      console.log(name.value)
    }


    // const updatename = (e) => {
    //   // console.log(e.target.value)
    //   name.value = e.target.value
    // } ---------> v.model 로 대체

    //원하는 변수 리턴을 해줘야 template 에서 접근이 가능해짐 
    return {
      name,
      name2,
      onsubmit,
      // great
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
