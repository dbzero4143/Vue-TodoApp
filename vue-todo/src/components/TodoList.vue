<template>
  <div>
      <ul>
        <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem.item" class="shadow">
          <button class="checkBtn" v-bind:class="{checkCompleted: todoItem.completed}" 
                                   v-on:click="todoCheck(todoItem, index)">check</button>
          <span v-bind:class="{textCompleted: todoItem.completed}">{{todoItem.item}}</span>
          <span>
            <button class="removeBtn" v-on:click="removeTodo(todoItem, index)">Delete</button>
          </span>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      todoItems: []
    }
  },
  methods: {
    removeTodo: function (todoItem, index) {
      console.log(todoItem, index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    todoCheck: function (todoItem) {
      todoItem.completed = !todoItem.completed;
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
      
    }
  },
  created: function () {
    if(localStorage.length>0){
      for(var i =0; i < localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
    
  }
}
</script>

<style>
ul {
  list-style-type: none;
}
.removeBtn{
margin-left:auto;
color: red;
}

.checkBtn {
  line-height: 45px;
  color: skyblue;
  margin-right: 5px;
}

.textCompleted{
text-decoration: line-through;
color: silver;
}

.checkCompleted {
  color: silver;
}
</style>