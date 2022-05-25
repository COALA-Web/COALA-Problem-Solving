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
         
          <b-dropdown v-model="language" aria-role="list">
            <template v-if="language=='Go'" #trigger>
              <b-button
                label="Go"
                type="is-primary"
              />
            </template>
            <template v-else-if="language=='Python3'" #trigger>
              <b-button
                label="Python3"
                type="is-primary"
              />
            </template>
            <template v-else-if="language=='JavaScript'" #trigger>
              <b-button 
                label="JavaScript"
                type="is-primary"
                
              />
            </template>
            <b-dropdown-item :value="'Go'" aria-role="listitem" @click="active_go()" >
              <div class="media">
                <div class="media-content" >
                    <h3>Go</h3>
                </div>
              </div>
            </b-dropdown-item>
              <b-dropdown-item :value="'Python3'" aria-role="listitem" @click="active_python()">
              <div class="media">
                <div class="media-content">
                  <h3>Python3</h3>
                </div>
              </div>
            </b-dropdown-item>
            <b-dropdown-item :value="'JavaScript'" aria-role="listitem" @click="active_javaScript()">
              <div class="media">
                <div class="media-content">
                    <h3>JavaScript</h3>
                </div>
              </div>
            </b-dropdown-item>

        </b-dropdown>


        </div>
        <div class="column">
          <img src="./assets/account.png"/>
          <img src="./assets/home.png"/>
          <img src="./assets/dashboard.png"/>
        </div>

      </div>
      
    </div>
    
    <div class="contents" @mouseup="verticalMsup()" @mousemove="verticalMove">
      <div class="guide-section" :style="guideStyle">
        <h6 class="guide-section-title"><b>문제 설명</b></h6>
        <hr>
        <ProblemOne/>
      </div>
      <div class="gutter-vertical" id="resize" @mousedown="verticalMsdwn()"   >
        <!-- <p> {{click}}</p>
        <p> {{counter}}</p> -->

      </div>
      <div class="run-section" :style="runStyle">
        <div class="editor-section">
          <h6 class="editor-section-title"><b>Solution.cpp {{click}}</b></h6>
          <div class="editor-section-contents">
            <textarea v-model="content" id="editor"></textarea>
          </div>    
        </div>
      </div> 
    </div>

    <div class="bottom-section" >
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
import ProblemOne from './components/ProblemOne.vue';
import * as CodeMirror from 'codemirror';
import 'codemirror/lib/codemirror.css';
import 'codemirror/theme/eclipse.css';
import 'codemirror/mode/javascript/javascript.js';
// import 'codemirror/mode/clike/clike.js'; // not working
import 'codemirror/mode/python/python.js';
import 'codemirror/mode/go/go.js';


export default {
  name: 'App',
  data(){
    return{
      topic : "알고리즘 문제",
      content: 'def solution(id_list, report, k):\n\tanswer = []\n\treturn answer\n',
      language: "Python3",
      click: false,
      counter: 0,

      
      guideStyle:{
        backgroundColor : '#F0FFF0',
        width: 'calc(50% - 8px)'
      },
      runStyle:{
        width:'calc(50% - 8px)'
      },
      windowWidth: window.innerWidth,
    }
  },
  components: {
    ProblemOne
  },
  mounted(){
    this.cm = CodeMirror.fromTextArea(document.getElementById('editor'),{
      lineNumbers: true,
      mode: 'python',
      theme: 'eclipse',
    });
  },
  methods: {
    active_go(){
      // alert("Go");
      this.cm.setOption('mode','go');
      this.content = "func solution(id_list []string, report []string, k int) []int {\n\treturn []int{}\n}\n\n\n\n"
      this.cm.setOption('value',this.content);
    },
    active_python(){
      // alert("python");
      this.cm.setOption('mode','python')
      this.content = "def solution(id_list, report, k):\n\tanswer = []\n\treturn answer\n";
      this.cm.setOption('value',this.content);
    },
    active_javaScript(){
      // alert("javascript");
      this.cm.setOption('mode','javascript')
      this.content = "function solution(id_list, report, k) {\n\tvar answer = [];\n\treturn answer;\n}\n";
      this.cm.setOption('value',this.content);
    },
    verticalMsdwn(){
      this.click = true;
      console.log('d');
    },
    verticalMsup(){
      this.click = false;
    },
    verticalMove(event){
      let mouseX = event.clientX;

      let halfGutterPercent = (8/this.windowWidth)*100+0.1;
      let widthPercent = (mouseX / this.windowWidth) * 100;
      
      // console.log(widthPercent-gutterPercent);
      // console.log(100-widthPercent+gutterPercent);

      
      if(this.click == true){
        console.log('work');
        this.guideStyle.width=(widthPercent-halfGutterPercent)+'%';
        this.runStyle.width=(100-widthPercent-halfGutterPercent) + '%';
      }
    }
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
  /* --test-value: 50%; */
  width: calc(50% - 8px);
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
.gutter-vertical{
  width: 16px;
  height: 100%;
  background-image: url(./assets/gutter.png);
  display: inline-block;
}
.run-section{
  width: calc(50% - 8px);
  height: 100%;
  display: inline-block;
  
}
.editor-section{
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.editor-section-title{
  font-size: 18px;
  margin: 1em 30px;
}
.editor-section-contents{
  width: 100%;
  height: 100%;
  overflow: scroll;
  top: 0;
  left: 0;
}
.CodeMirror {
    font-family: monospace;
    height: 100%;
    color: black;
    direction: ltr;
}
.bottom-section{
  margin: 1em;
  height:8%;
  width:100%;
}


</style>
