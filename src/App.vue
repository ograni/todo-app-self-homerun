<template>
  <!-- 3. 컴포넌트 태그를 html 영역에 등록시켜준다. -->
  <div id="app">
    <todo-header></todo-header>
    <!-- <todo-input v-on:하위컴퍼넌트에서 발생시킨 이벤트 이름="현재 컴포넌트 메서드 이름"></todo-input> -->
    <todo-input v-on:add="addTodoItem"></todo-input>
    <!-- <todo-list v-bind:내려보낼 프롭스 속성 이름="현재 컴포넌트의 데이터 속성"></todo-list> -->
    <todo-list v-bind:propsdata="todoItems" v-on:remove="removeTodoItem"></todo-list>
    <todo-footer v-on:removeAll="clearAll"></todo-footer>
  </div>
</template>

<script>
// 1.컴포넌트를 app기vue 파일에 컴포넌트를 등록해주기 위해 import 한다.
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  data() {
      return {
          todoItems:[]
      }
  },
  methods: {
    addTodoItem(value) {
			// 배열에 추가
			this.todoItems.push(value);
			// 저장소에 저장
			localStorage.setItem(value, value);
    },
    removeTodoItem(todoItem, index){
      console.log('1234')
      this.todoItems.splice(index, 1)
      localStorage.removeItem(todoItem);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
  created () {
      if(localStorage.length > 0){
          for (var i = 0; i < localStorage.length; i++){
              // console.log(localStorage.key(i));  
              this.todoItems.push(localStorage.key(i))
          }
      };
  },
  components : {
    // 2. import한 파일을 컴포넌트로 등록해 준다.
      'todo-header' : TodoHeader,
      'todo-input' : TodoInput,
      'todo-list' : TodoList,
      'todo-footer' : TodoFooter
      // '컴포넌트 이름' : 컴포넌트 내용,
  },
  
}
</script>

<style>
body {
    text-align: center;
    background-color: #F6F6F8;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
  }
</style>
