<template>
  <li class="finish">
    <input type="checkbox" checked @click="handleContinue"/>
    <span>{{content}}</span>
  </li>
</template>

<script>
export default {
  name: 'todoFinish',
  props: ['content','num'],
  methods: {
    handleContinue: function(){
      this.$emit('continue',this.num)
    }
  }
}
</script>

<style scoped>
  .finish{
    list-style: none;
  }
</style>
