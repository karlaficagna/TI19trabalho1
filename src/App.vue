<template>
  <div id="app">
    <Header />
    <CardConversor :moedaD="USD" :moedaR="BRL" :moedaE="EUR" />
    <Form />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import CardConversor from "./components/CardConversor.vue";
import Form from "./components/Form.vue";
export default {
  name: "App",
  components: {
    Header,
    CardConversor,
    Form,
  },

  methods: {
    getMoeda: async function () {
      const result = await fetch(" https://docs.awesomeapi.com.br/api-de-moedas")
        .then((res) => res.json())
        .then((res) => res)
        .catch((error) => {
          return {
            error: true,
            message: error,
          };
        });
      console.log(result);
      if (!result.error) {
        this.moeda = result;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
