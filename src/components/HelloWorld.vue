<template>
  <div class="hello">
    <h1>{{msg}}</h1>
    <p>{{obj.name}}</p>
    <p>{{obj.age}}</p>
    <p>{{obj.home}}</p>
    
  </div>
  
</template>

<script>
export default {
  data(){
    return {
      msg: '你一定要这么做吗老六？',
      obj: {
        name:'快来看',
        age:99999999,
        home:'香港'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1{
    color: blueviolet;
    font-style: italic;
    font-size: 70px;
  }
  p {
    color: violet;
    font-size: 100px;
  }
</style>
