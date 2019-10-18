<template>
  <ul id="NodeVersion" class="mt1">
    <li>主网版本<br/><span>Mainnet Version : {{items}}</span></li>
    <li v-if="items">主网版本<br/><span>Mainnet Version : {{items.mainnet}}</span></li>
    <li v-if="items" class="green">测试网版本<br/><span>Testnet Version : {{items.testnet}}</span></li>
  </ul>
</template>

<script>
// /api/consensus
export default {
  name: 'NodeVersion',
  data () {
    return {items :""}
  },
  mounted () {
    this.getVersion();
  },
  methods: {
    getVersion:function() {
      this.$http.get('/api/consensus').then(function(res){
        this.items = res.data;
      },function(){
        this.version = {mainnet:"/Neo:2.10.2/",testnet:"/Neo:2.10.1/"};
        console.log("未调用到api");
      });
    }
  }
}
</script>

<style>
#NodeVersion{
  padding: 0;
}
#NodeVersion li{
  display: inline-block;
  margin: 25px;
  width: 220px;
  height: 61px;
  list-style: none;
  font-size: 20px;
  color:#00af92;
  background: #FFFFFF;
  line-height: 1.3;
  letter-spacing: .3px;
  padding-top: 9px;
}
#NodeVersion li.green{
  color:#FFFFFF;
  background: #007a66;
  box-shadow: 1px 1px 4px #D7D6D6;
}
#NodeVersion li span{
  font-size: 14px;
}
</style>
