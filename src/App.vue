<template>
  <div id="app" class="container t-ce">
    <NavBar />
    <NodeVersion class="mt1"/>
    <NodeList />
    <img src="./assets/logo.png" class="mt1" width="114" height="50">
  </div>
</template>

<script>
import NavBar from './components/NavBar'
import NodeList from './components/NodeList'
import NodeVersion from './components/NodeVersion'

export default {
  name: 'App',
  components: {
    NavBar,NodeList,NodeVersion
  }
}
</script>

<style>
body,html{
    font-family: PingFang SC,STHeiti,Tahoma, "Microsoft YaHei",arial, sans-serif;
    margin: 0;
    line-height: 2;
}

body {
    background: #E3EEE3;
    line-height: 2.4;
    background-image: url("./assets/syncbg.svg");
    background-position: top center;
    background-size: 100%;
    background-repeat: no-repeat;
    font-weight: 300;
    letter-spacing: .8px;
}

a {
    cursor: pointer;
    color: #57AF06;
    text-decoration: none;
}

a:hover {
    color: #308600;
    text-decoration: underline;
    text-shadow: 0 0 5px #99FF66;
}

.container{
    min-width: 600px;
    max-width: 1200px;
    margin: auto;
}

.mt1{margin-top: 100px;}
.mt2{margin-top: 40px;}
.mt3{margin-top: 20px;}
.mt4{margin-top: 10px;}

.mb1{margin-bottom: 100px;}
.mb2{margin-bottom: 40px;}
.mb3{margin-bottom: 20px;}

.f1{font-size: 36px;}
.f2{font-size: 24px;}
.f3{font-size: 14px;}
.fw-b{font-weight: bolder;}
.fw-l{font-weight: lighter;}
.t-le{text-align: left;}
.t-ce{text-align: center;}
.t-ri{text-align: right;}
.t-white{color: #FFFFFF;}
.t-black{color: #000000;}
.t-green{color: #57AF06;}
</style>