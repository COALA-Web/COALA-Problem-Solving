<template>
<body>
  <!-- 유리님꺼 -->
  <div class="nav_bar" style="height:5%; width:100%; background-color: #FAEBD7" >
    <p>임시 nav bar </p>
  </div>

  <div class="main theme">
    <div class="problem-nav">
      <p>임시 problem nav bar </p>
    </div>
    
    <div class="contents">
      <div class="guide-section"></div>
      <div class="gutter-horizontal"></div>
      <div class="run-section"></div> 
    </div>

    <div class="bottom-section">
      <p>bottom section</p>
    </div>
  </div>

</body>
</template>

<script>


export default {
  name: 'App',
  components: {
    
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
html, body {
  height: 100%;
}
.main {
  height:100%;
  width:100%;
}
.theme {
  background-color: #F0FFF0;
}
.problem-nav{
  background-color: #00FFFF;
  height:5%;
  width:100%;
}
.contents{
  height:80%;
  width:100%;
}
.guide-section{
  background-color:#666666;
  width: calc(40% - 12px);
  height: 100%;
  display: inline-block;
}
.gutter-horizontal{
  width: 24px;
  height: 100%;
  background-color: #643563;
  display: inline-block;
}
.run-section{
  background-color:#126952;
  width: calc(60% - 12px);
  height: 100%;
  display: inline-block;
}
.bottom-section{
  height:10%;
  width:100%;
  background-color: #7FFFD4;
}


</style>
