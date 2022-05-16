<template>
<body>
  <!-- 유리님꺼 -->
  <div class="nav_bar" style="height:5%; width:100%; background-color: #FAEBD7" >
    <p>임시 nav bar </p>
  </div>

  <div class="main theme">
  
    <div class="problem-nav">
      <div class="columns is-variable is-1-mobile is-0-tablet is-2-desktop is-8-widescreen">
        <div class="column is-one-quarter">
          <br>  <p style="text-indent: 20px;font-size:25px"><b>{{topic}}</b></p>
        </div>
        <div class="column is-two-fifths">
        </div>
        
        <div class="column">
          <div class="buttons">
            <b-button type="is-light">light</b-button>
            <b-button type="is-dark">dark</b-button>
          </div>
        </div>
        <div class="column">
          <b-dropdown aria-role="list">
              <template #trigger="{ active }">
                  <b-button
                      label="C++"
                      type="is-primary"
                      :icon-right="active ? 'menu-up' : 'menu-down'" />
              </template>
              <b-dropdown-item aria-role="listitem">Python</b-dropdown-item>
              <b-dropdown-item aria-role="listitem">JAVA</b-dropdown-item>
              <b-dropdown-item aria-role="listitem">GO</b-dropdown-item>
          </b-dropdown>
        </div>
        <div class="column">
          <img src="./assets/account.png"/>
          <img src="./assets/home.png"/>
          <img src="./assets/dashboard.png"/>
        </div>

      </div>
      
    </div>
    
    <div class="contents">
      <div class="guide-section">
        <h6 class="guide-section-title"><b>문제 설명</b></h6>
        <hr>
        <ProblemOne/>
          
        
      </div>
      <div class="gutter-horizontal"></div>
      <div class="run-section"></div> 
    </div>

    <div class="bottom-section">
      <div class="columns">
        <div class="column is-one-quarter">
          <div class="buttons">
            <b-button type="is-primary" inverted>질문하기</b-button>
            <b-button type="is-primary" inverted>코드 리뷰 보기</b-button>
          </div>
        </div>
        <div class="column is-half"></div>
        <div class="column is-one-quarter">
          <div class="buttons">
            <b-button type="is-primary" inverted>다른 사람 풀이보기</b-button>
            <b-button type="is-primary" inverted>초기화</b-button>
            <b-button type="is-primary" inverted>실행</b-button>
            <b-button type="is-primary" inverted>제출</b-button>
          </div>
        </div>

          

      </div>
    </div>
  </div>

</body>
</template>

<script>
import ProblemOne from './components/ProblemOne.vue'


export default {
  name: 'App',
  data(){
    return{
      topic : "알고리즘 문제"
    }
  },
  components: {
    ProblemOne
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
  height:7%;
  width:100%;
}

.contents{
  height:80%;
  width:100%;
}
.guide-section{
  /* background-color:#666666; */
  width: calc(50% - 12px);
  height: 100%;
  display: inline-block;
  padding: 1em;
  overflow:scroll
}
.guide-section-title{
  font-family: arial;
  font-size: 18px;
  margin: 1em 0px;
  text-align: center;
}
.gutter-horizontal{
  width: 24px;
  height: 100%;
  background-color: #643563;
  display: inline-block;
}
.run-section{
  background-color:#126952;
  width: calc(50% - 12px);
  height: 100%;
  display: inline-block;
}
.bottom-section{
  height:10%;
  width:100%;
}


</style>
