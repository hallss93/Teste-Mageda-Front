<template>
  <div class="home">
    <div id="caixa">
      <div id="caixa-bkg"></div>
      <img id="imagem" src="./../assets/sol.png" alt="Sol" />
      <img id="arvore" src="./../assets/arvore.png" alt="Árvore" />
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
    window.onload = function() {
      document
        .getElementById("caixa-bkg")
        .setAttribute("style", "height: " + window.innerHeight + "px");
    };
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
      let j = alturaTotal - (alturaTotal / 100) * percentual;
      let percentual_wid = window.innerWidth;
      if (percentual > 30) {
		  percentual = 30;
	  }
      let i = alturaTotal - (alturaTotal / 100) * percentual;
      document
        .getElementById("imagem")
        .setAttribute("style", "transform: rotate(" + deg + "deg);");

      document
        .getElementById("caixa-bkg")
        .setAttribute("style", "height: " + i + "px");
      if (percentual < 30)
        document
          .getElementById("arvore")
          .setAttribute(
            "style",
            "top: " +
              (j - 200) +
              "px;display:block;right:" +
              (percentual_wid - (j - 100)) +
              "px"
          );
      else
        document
          .getElementById("arvore")
          .setAttribute(
            "style",
            "top: " +
              (i - 200) +
              "px;display:block;right:" +
              (percentual_wid - (j - 100)) +
              "px"
          );
    };
  }
};
</script>
<style>
#caixa {
  background: green;
  height: 2000px;
}
#imagem {
  position: fixed;
  margin: 20px;
  left: 20%;
  z-index: 2;
  width: 200px !important;
}
body {
  margin: 0px;
}
h3 {
  position: fixed;
  right: 20%;
}
#caixa-bkg {
  background-image: url("./../assets/nuvens.jpg");
  position: fixed;
  top: 0;
  z-index: 1;
  left: 0;
  width: 100%;
}
#arvore {
  top: 2000px;
  display: none;
  height: 200px;
  z-index: 9;
  position: fixed;
}
</style>
