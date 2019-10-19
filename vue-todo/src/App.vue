<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input></todo-input>
    <todo-list></todo-list>
    <todo-footer></todo-footer>
  </div>
</template>

<script>
//import는 주소에 적혀있는 파일의 내용을 TodoHeader라는 이름으로 다 가져오는 기능을 가지고 있다.
//html에서는 html파일안에 header/body/footer 다 넣었지만
//Vue에서는 따로 만들어서 하나의 파일에 합친다.
//이유는 개별적으로 만든것들이 더 관리하기 용이하기 때문이다.
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  //가져온 TodoHeader 파일을 App.vue에 적용시키기 위해 컴포넌트를 적는다.
  components:{
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>
body {
  text-align:center;
  background-color: #F6F6F6;
}
input {
  border-style: groove;
  width:200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
