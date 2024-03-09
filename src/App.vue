<template>
  <app-header></app-header>
  <div class="container">
    <compTransition></compTransition>

  </div>
  <app-footer></app-footer>

 
</template>

<script>
// import compTransition from './components/transition/one.vue'
import compTransition from './components/transition/two.vue'
export default{
  components:{
    compTransition
  }
}
</script>
<style>
body{
    padding: 0;
    margin: 0;
}
.container{
    min-height: 73vh;
    box-sizing: border-box;
    padding: 20px;

}
button{
    padding: 10px;
    background: green;
    cursor: pointer;
    border-radius: 10%;
    border: none;
}
button:hover{
    background: yellow;
}
</style>