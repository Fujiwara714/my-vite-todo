<script setup>
import { ref } from 'vue';
const todoRef = ref('');
const todoListRef = ref([]);

const addTodo = () => {
  // IDを簡易的にミリ秒で登録する
  const id = new Date().getTime();

  // 配列に入力TODOを格納
  todoListRef.value.push({
    id: id,
    title: todoRef.value,
  });

  // ローカルストレージに登録
  localStorage.todoList = JSON.stringify(todoListRef.value);
};
</script>

<template>
  <div class="box_input">
    <input type="text" class="todo_input" v-model="todoRef" placeholder="＋　TODOを入力" />
    <button class="btn" @click="addTodo">追加</button>
  </div>
</template>

<style scoped>
.box_input {
  margin-top: 20px;
}

.todo_input {
  width: 300px;
  margin-right: 8px;
  padding: 8px;
  font-size: 18px;
  border: 1px solid #aaa;
  border-radius: 6px;
}

.btn {
  padding: 8px;
  background-color: #03a9f4;
  border-radius: 6px;
  color: #fff;
  text-align: center;
  font-size: 14px;
}
</style>
