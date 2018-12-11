<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <!--App컴포넌트로 이벤트로 전달 할 수 있도록 설정 v-on-->
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
  data(){
    return{
      todoItems:[]
  }
},
//이제 App.vue에서 중앙관리화 하기 떄문에 리스트에 있던 스크립트 코드를 여기로 가져온다.
   created(){
                if(localStorage.length>0){
                        for(var i=0;i<localStorage.length;i++){
                                this.todoItems.push(localStorage.key(i));
                        }
                }
         
        },

methods:{

    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },
		addTodo(todoItem) {
			localStorage.setItem(todoItem, todoItem);
			this.todoItems.push(todoItem);
		},
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  },

 
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>
body {
  text-align: center;
  background-color:aliceblue;
} 
input {
  border-style:groove;
  width: 200px;
}

button{
  border-style:groove;

}

.shadow{
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
}
</style>
