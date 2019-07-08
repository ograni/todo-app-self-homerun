<template>
  <!-- 3. 컴포넌트 태그를 html 영역에 등록시켜준다. -->
  <div id="app">
    <todo-header></todo-header>
    <todo-input></todo-input>
    <todo-list></todo-list>
    <todo-footer></todo-footer>
  </div>
</template>

<script>
// 1.컴포넌트를 app기vue 파일에 컴포넌트를 등록해주기 위해 import 한다.
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
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

</style>
