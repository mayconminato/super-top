<template>
  <div class="">
    <router-view :websocket='websocket' @criaWS='criaWS'></router-view>
  </div>

</template>

<script>

export default {
  data () {
    return {
      websocket: null
    }
  },
  methods: {
    criaWS(nome){
      let rota = this.$router;
      this.websocket = new WebSocket('ws://172.29.80.15:8080/StopWeb/websocket?nome=' + nome);
      this.escutaWS();
      // this.websocket.onmessage = function(msg){
      //   // console.log(msg.data);
      //
      //   console.log(JSON.parse(msg.data));
      //
      //   let resposta = JSON.parse(msg.data);
      //   if(resposta.funcao == "newRodada"){
      //     this.$router.push({ name: 'jogo'});
      //   } else if (true) {
      //     rota.push({ name: 'jogo'});
      //   }
      // }
    },
    escutaWS(){
      this.websocket.onmessage = function(msg){
        // console.log(msg.data);

        console.log(JSON.parse(msg.data));

        let resposta = JSON.parse(msg.data);
        if(resposta.funcao == "newRodada"){
          this.$router.push({ name: 'jogo'});
        } else if (true) {
          rota.push({ name: 'jogo'});
        }
      }
    },
  }
}
</script>

<style>
</style>
