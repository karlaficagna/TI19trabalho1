<template>
  <b-row>
    <b-col md="4">
      <div class="card">
        <h5 class="card-title">R$</h5>
        <p class="card-text">Cotação do {{ moedaD }} {{ moedaE }} hoje</p>
        <p class="card-text2">Moeda</p>
        <select class="form-select" aria-label="Seletor de moeda" v-model="moedaD">
          <option value="USD">USD (Dólar Americano)</option>
          <option value="EUR">EUR (Euro)</option>
        </select>
      </div>
    </b-col>
  </b-row>
</template>
<script>
export default {
  name: "Card",
  props: ["moedaD", "moedaR", "moedaE"],
};
</script>

<style>
.card {
  width: 100%;
  height: 180px;
  margin-left: 550px;
  margin-top: 36px;
}
</style>
