<template>
    <div>
     <input type="text" v-model="newTodoItem">   
     <button v-on:click="addTodo">ADD</button>
        
    </div>
</template>

<script>

    export default{
        data(){
            return{
                newTodoItem:''
            }
        },

        methods:{
            addTodo(){
                if(this.newTodoItem !==""){
                    var value=this.newTodoItem && this.newTodoItem.trim();
                    localStorage.setItem(value,value);
                    this.clearInput();
                }
            },
            clearInput(){
                this.newTodoItem='';
            }
                //console.log(this.newTodoItem);
                //localStorage.setItem(this.newTodoItem,this.newTodoItem);
            }
        }
    
</script>

<style>

</style>