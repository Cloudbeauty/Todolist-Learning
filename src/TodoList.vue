<template>    
  <div class="todolist">
    <h1>Todolist</h1>
    <div>
        <input v-model="inputValue"/>
        <button @click="handleSubmit">提交</button>
    </div>
    <h1>正在进行</h1>
    <!--将循环值item传入属性content 绑定删除、完成事件-->
    <ul>
      <todo-item 
         v-for="(item,index) of list"            
         :key="index" 
         :content="item"
         :index="index"
         @delete="handleDelete"
         @finish="handleFinish">
      </todo-item>    
    </ul>
    <hr/>
    <h1>已经完成</h1>
      <ul>
        <todo-finish
        v-for="(item,num) in lists"
        :key="num"
        :content="item"
        :num="num"
        @continue="handleChange">
        </todo-finish>    
      </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem'         
import TodoFinish from './components/TodoFinish'         

export default { 
  components: {
    'todo-item': TodoItem,        //注册局部组件
    'todo-finish' : TodoFinish 
  },
  data () {                
    return {               
      inputValue:'',
      list: [],
      lists: []
    }
  },
  methods: {             
    handleSubmit: function(){
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handleFinish: function(index){
      this.lists.push(this.list[index])
      this.list.splice(index,1)
    },
    handleDelete: function(index){
      this.list.splice(index,1)
    },
    handleChange: function(num){
      this.list.push(this.lists[num])
      this.lists.splice(num,1)
    }
  }
}
</script>

<style scoped>
  .todolist{
    width:60%;
    margin:auto auto;
    border: 1px solid black;
    padding: 20px;
  }
</style>
