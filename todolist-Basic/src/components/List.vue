<template>
    <div>
        <!-- todo list -->
         <!-- for 문 할일내용 반복할때, 수정삭제할 때 인덱스값 필요 -->
         <!-- pa-3 : padding all 3 -->
        <v-card
            class="pa-3"
            v-for = "(list, index) in todolist"
            :key="index"
        >
            <p>{{list.memo}}</p>
            <v-btn fab flat small color="green"><i class="fas fa-check"></i></v-btn>
            <v-btn fab flat small color="blue"><i class="fas fa-redo-alt"></i></v-btn>
            <v-btn fab flat small color="red"><i class="fas fa-trash-alt"></i></v-btn>

        </v-card>
    </div>
</template>


<script>
    export default {
        props : ["todolist"]
    }
</script>
