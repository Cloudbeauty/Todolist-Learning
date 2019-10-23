<template>
  <li class="item">
    <input type="checkbox" @click="handleContent"/>
    <span @click="handleClick">{{content}}</span>
  </li>
</template>

<script>
export default {
  name: 'todoItem',
  props: ['content','index'],
  methods: {
    handleClick: function(){
      this.$emit('delete',this.index)     //$emit实现子组件向父组件传递的属性
    },
    handleContent: function(){
      this.$emit('finish',this.index)
    }
  }
}
</script>

<style scoped>
  .item{
    list-style: none;
  }
</style>
