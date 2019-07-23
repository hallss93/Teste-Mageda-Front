<template>
  <div class="home">
    <div id="caixa">
      <img id="imagem" src="./../assets/sol.png" alt="Sol" />
      <h3>Ângulo: {{angulo}}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      angulo: 0
    };
  },
  created() {
    var that = this;
    document.onscroll = function(e) {
      // height da caixa e o tamanho da tela atual
      let alturaTotal =
        document.getElementById("caixa").offsetHeight - window.innerHeight;
      // percentual do scroll baseado na altura da tela com a atualra geral
      let peca = alturaTotal / 100;
      let percentual = window.scrollY / peca;
      //   angulo de rotação de acordo com o scroll máximo 360 default
      let deg = (360 / 100) * percentual;
      that.angulo = deg.toFixed(1);
      document
        .getElementById("imagem")
        .setAttribute("style", "transform: rotate(" + deg + "deg);");
    };
  }
};
</script>
<style>
#caixa {
  background: #a7d0ef6e;
  height: 2000px;
}
#imagem {
  position: fixed;
  margin: 20px;
  left: 20%;
  width: 200px !important;
}
body {
  margin: 0px;
}
h3 {
  position: fixed;
  right: 20%;
}
</style>
