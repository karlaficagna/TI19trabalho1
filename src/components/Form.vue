<template>
  <div>
    <div class="title">
      <h5>Faça a conversão de valores</h5>
    </div>
    <div class="sub-title">
      <p>Valor a ser convertido</p>
    </div>

    <b-button-toolbar aria-label="Barra de conversao" class="input1">
      <b-input-group size="sm-4" prepend="USD - $">
        <b-form-input
          value=" "
          class="valorConverter"
          v-model="moedaD_value"
        ></b-form-input>
      </b-input-group>
      <b-button @click="onChangeFlag">Converter</b-button>
    </b-button-toolbar>

    <div class="sub-title2">
      <p>Valor em reais</p>
    </div>
    <b-button-toolbar aria-label="Barra de valor convertido" class="input2">
      <b-input-group size="sm-8" prepend="BRL - R$">
        <b-form-input
          value=" "
          class="valorConvertido"
          v-model="moedaR_value"
        ></b-form-input>
      </b-input-group>
    </b-button-toolbar>
  </div>
</template>

<script>
export default {
  name: "Form",
  props: ["moedaD", "moedaR", "moedaE"],
  data() {
    return {
      moedaD_value: "",
      moedaR_value: 0,
    };
  },
  methods: {
    converter: async function () {
      fetch(" http://economia.awesomeapi.com.br/json/last/USD-BRL").then((res) =>
        res.json(this.tofixed(2))
      );
    },
  },
};
</script>

<style>
.input1 {
  align-items: center;
  position: relative;
  margin-left: 600px;
  margin-top: 0px;
}
.input2 {
  align-items: center;
  position: relative;
  margin-left: 600px;
  margin-top: 0px;
}

.title {
  margin-top: 50px;
  margin-right: 60px;
}
.sub-title {
  margin-top: 30px;
  margin-right: 155px;
}
.sub-title2 {
  margin-top: 30px;
  margin-right: 200px;
}
</style>
