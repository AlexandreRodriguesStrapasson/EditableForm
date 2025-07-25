<template>
  <div id="a4">
    
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style scoped>
#a4 {
  width: 210mm;
  height: 297mm;

  border: 1px solid black;
  
  background-image: url('/formModel.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;

  margin: 20px auto;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  
  box-sizing: border-box; 
  padding: 10mm;
}
</style>