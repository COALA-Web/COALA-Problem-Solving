<template>
<div class="nav">
    <img src="../assets/coala.png"/>
    <a href="#" style="margin-left: 30%;" >추천학습</a>
    <a href="#">|</a>
    <a href="#">선택학습</a>
    <a href="#">|</a>
    <a href="#">게시판</a>
    <a href="#">|</a>
    <a href="#">대회</a>
    <div style="margin-left: 30%;">
    <img  src="../assets/bell.png"/>
    <img src="../assets/my.png"/>
    </div>
</div>
</template>

<script>
export default{
    name:'Header'
}
</script>

<style>
.nav{
    background-color: #3334;
    
}
.nav a{  
    float: left;
    color: black;
    padding: 14px 16px;
    font-size: 22px;
    text-align: center;
    text-decoration: none;
}
.nav img{
    float: right;
    padding: 0px 3px;
    width: 70px; 
    height: 60px;
}
</style>
