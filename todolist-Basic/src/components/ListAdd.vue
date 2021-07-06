<template>
    <div>
        <!-- todolist add
        할일 입력하는 텍스트필드
        추가버튼 들어가야함 -->

        <!-- v-model을 통해 뷰인스턴스와 통신 -->
        <v-textarea
          outlined
          
          v-model = "memo"
          label="Plz write TO DO LIST "
          value=""
        ></v-textarea>

        <v-btn @click="listAdd"> 투두리스트 추가 </v-btn>

    </div>
</template>

<script>
export default {
    data(){
        return {
            // v-model 로 바인딩 시킨 memo 가 들어감
            memo : null
        }
    },
    methods : {
        listAdd() {
            console.log('리스트 추가')
            if(this.memo === null){
                alert("할일을 입력해주세요")
            }else{
                // memo 를 인자로 받고, 에밋을 통해 부모로 보냄
                this.$emit('listAdd', this.memo)

            }
            
        }
    }
    
}
</script>