<template>
  <b-col>
    <b-form-group>
      <b-form-select v-model="selectMoeda">
        <b-form-select-option :value="USD">Dolar</b-form-select-option>
        <b-form-select-option :value="EUR">Euro</b-form-select-option>

        <b-form-select-option>
          {{ selected === "USD" ? "dolar" : "euro" }}
        </b-form-select-option>
      </b-form-select>
    </b-form-group>
  </b-col>
</template>
<script>
export default {
  name: "SelectMoeda",
  props: {
    getMoedaSelecionada: Function,
  },
  data: function () {
    return {
      moeda: [],
      selected: dolar,
      euro,
    };
  },
  created: function () {
    this.getMoeda();
  },
  updated: function () {
    this.getMoedaSelecionada(this.selected);
  },
  methods: {
    getMoeda: async function () {
      const result = await fetch("https://docs.awesomeapi.com.br/api-de-moedas")
        .then((res) => res.json())
        .then((res) => res)
        .catch((error) => {
          const objError = {
            error: true,
            message: error,
          };
          return objError;
        });
      if (!result.error) {
        this.moeda = result;
      }
    },
  },
};
</script>
