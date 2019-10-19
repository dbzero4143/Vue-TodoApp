<template>
  <div class="inputbox shadow">
      <input type="text" v-model="newTodoItem">
      <span class="addContainer" v-on:click="addTodo">
          <i class="fas fa-plus addBtn">+</i>
      </span>
  </div>
</template>

<script>
export default {
    data: function () {
        return {
            newTodoItem: ""
        }
    },
    methods: {
        //로컬스토리지에 input에 적은 값을 저장하는 기능을 가지고있는 메소드
        addTodo: function () {
            localStorage.setItem(this.newTodoItem,this.newTodoItem)
            //현재 여기서 사용되는 this는 data의 내용도 참조가 가능하고
            //또다른 methods도 참조가 가능하다.
            //전부 같은위치의 인스턴스이기 때문이다. 
            this.clearInput();
        },
        //input버튼을 누르면 로컬스토리지에 저장되고 
        //input box는 다시 빈칸으로 만드는 기능을 가지고있는 메소드
        clearInput: function () {
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
input:focus {
    outline:none;
}

.inputbox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}

.inputbox input {
    border-style:none;
    font-size:0.9rem;
}

.addContainer {
    float:right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn {
    color: #3cba54;
    vertical-align: middle;
}
</style>