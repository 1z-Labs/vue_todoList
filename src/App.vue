<template>
  <img src="./assets/logo.png">
  <div class="container">
    <h1>TodoList</h1>
    <!--form 태그-->
    <form @submit.prevent="Submit" class="d-flex">
      <!--할일 추가-->
      <div class="flex-grow-1">
        <input class="form-control" type="text" v-model="todo" placeholder="할 일을 적어주세요!">
      </div>
      <!--버튼-->
      <div>
        <button class="btn btn-primary">추가하기</button>
      </div>
    </form>

    <!--리스트를 표시함-->
    {{ todolist }}

    <!--리스트를 정돈하여 출력할 거!-->
    <ul class="list-group" v-for="i in todolist" v-bind:key="i.id">
      <li class="list-group-item">{{ i.sbj }}</li>
    </ul>
  </div>
</template>

<script>
import {ref} from 'vue'

export default {
  setup(){
    let todo = ref(""); // 할 일 입력 값을 저장
    let todolist = ref([
      {id: 1, sbj: '할일1'},
      {id: 2, sbj: '할일2'},
      {id: 3, sbj: '할일3'},
    ]);

    // 할 일을 추가
    var Submit = () => {
      todolist.value.push({
        id: Date.now(), // 현재 시간 사용
        sbj: todo.value // 할 일 내용
      });
    }

    return {
      todo,Submit,todolist,
    };
  }
}
</script>

<style>
</style>
