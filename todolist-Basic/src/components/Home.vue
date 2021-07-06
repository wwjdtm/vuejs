<template>
<v-container>
  <!-- {{todoList}} -->
  <v-layout row wrap>
    <!-- 화면 절반을 차지함 -->
    <v-flex xs6 pa-2>  
      <!-- v-card 는 클래스로 스타일 적용, v-flex 는 그냥 적용 -->
            <!-- 부모에 있는 todolist 를 보내줘야함
      todoList 라는 값을 :todolist 로 받음 
      @statusControl 신호를 받으면 statusConstrol함수실행-->
      <List
        :todolist = "todoList"
        @statusControl = "statusControl"
        @listDelete = "listDelete"
        />



    </v-flex>
    <!-- 나머지 절반을 차지함 -->
    <v-flex xs6 pa-2>

      <!-- 에밋을 듣는 장치 ,
          @listAdd 라는 에밋이 오면 listAdd 함수를 실행시켜!-->
      <ListAdd
        
        @listAdd = "listAdd"
      
      />




    </v-flex>


  </v-layout>

</v-container>
</template>

<script>
import List from './List'
import ListAdd from './ListAdd'

export default {
  components : {
    List,
    ListAdd
  },

  data() {
    return {
      // 자식 컴포넌트에서 에밋받은 값을 담을 array
      todoList : []
    }
  },

  methods : {
    listAdd(memo) {
      console.log('get!!!!')
      this.todoList.push({memo : memo , status : "created"})
    },
    statusControl(index,status){
      this.todoList[index].status = status
    },
    listDelete(index){
      // splice - > 그 요소부터 한개를 지움
      this.todoList.splice(index, 1)
    }
  }
}
</script>