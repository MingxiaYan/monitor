<template>
  <div>
    <div class="t-ri">
        <a v-on:click="changeNet()">主网 <small>MainNet</small></a>&nbsp;&nbsp;&nbsp;
        <a v-on:click="changeNet(2)">测试网 <small>TestNet</small></a>&nbsp;&nbsp;&nbsp;
        <a onclick="location.reload();">刷新 <small>Refresh</small></a>
    </div>
    <div class="table-con">
      <table id="NodeTable" class="table-s1 mt4">
        <thead>
          <tr>
            <th width="35%">Endpoint</th>
            <th width="20%">Block Height</th>
            <th width="15%">Lantency</th>
            <th width="15%">Type</th>
            <th width="15%">Version</th>
          </tr>
        </thead>
        <tbody v-for="item in items" :key='item.url'>
          <tr>
            <td>{{item.url}}</td>
            <td>{{item.height}}</td>
            <td>{{item.latency}}</td>
            <td>{{item.type}}</td>
            <td>{{item.version}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
// /api/seeds
export default {
  name: 'NodeList',
  data () {
    return {items :""}
  },
  mounted () {
    this.getList();
    // if(this.timer){
    //   clearInterval(this.timer);
    // }else{
    //   this.timer = setInterval(()=>{
    //     this.getList();
    //   },5000)
    // }
  },
  methods: {
    getList:function() {
      var net = !!window.location.hash?2:1;
      this.$http.get('/api/seeds').then(function(res){
        return res.data;
      }).then(function(data){
        this.items = net == 1? data.mainnet:data.testnet;
      });
    },
    changeNet:function(net) {
      window.location.hash = net?2:"";
      this.getList();
    }
  }
}
</script>

<style>
table {
    text-align: left;
    width: 100%;
}

.table-con{
    background: #FFFFFF;
    padding: 0px 15px;
}

.table-s1 {
    border-collapse: collapse;
}

.table-s1 th,
.table-s1 td {
    padding: 10px;
}

.table-s1 th {
    color: #222222;
    font-weight: 900;
    border-bottom: 1px solid #CDCDCD;
}

.table-s1 td {
    color: #333333;
    font-size: 15px;
}
</style>