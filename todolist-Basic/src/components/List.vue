<template>
    <div>
        <!-- todo list -->
         <!-- for 문 할일내용 반복할때, 수정삭제할 때 인덱스값 필요 -->
         <!-- pa-3 : padding all 3 -->

         <!-- :class="{'done' : list.status === 'done'}"
         class 바잉딩하고, done 클래스 설정, list의 status 가 done 일경우
         done 이라는 클래스가 적용되도록함 -->

        <v-card
            class="pa-3"
           
            :class="{'done' : list.status === 'done'}"
            v-for = "(list, index) in todolist"
            :key="index"
        >
            <p>{{list.memo}}</p>
             <!-- <p>{{list.status}}</p> -->
            <!-- 완료 / 버튼이 눌리면 statuscontrol 의 신호를 부모로 보냄-->
            <v-btn
            v-if="list.status === 'created'"
            @click="$emit('statusControl', index, 'done')" 
            fab flat small color="green"><i class="fas fa-check"></i></v-btn>

            <!-- 다시 되돌리기 -->
            <v-btn
            v-else 
            @click="$emit('statusControl', index, 'created')" 
            fab flat small color="blue"><i class="fas fa-redo-alt"></i></v-btn>

            <!-- 삭제 -->
            <v-btn 
            @click="$emit('listDelete', index)" 
            fab flat small color="red"><i class="fas fa-trash-alt"></i></v-btn>

        </v-card>
    </div>
</template>


<script>
    export default {
        props : ["todolist"]
    }
</script>

// scoped 를 설정하면 현재 파일 내에서만 css 적용됨
<style scoped> 
.done {
    background: rgba(0,0,0,0.1);
}
.done p{
    text-decoration: line-through;
    color: rgba(0,0,0,0.5);
}


</style>