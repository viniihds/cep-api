<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: "",
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const res = await axios.get(url);
      this.endereco = res.data;
    },
  },
};
</script>

<template>
  <h1>Buscar CEP</h1>
  <form @submit.prevent="buscar">
    <input type="text" placeholder="Digite seu CEP" />
    <button type="submit">Buscar</button>
  </form>
  <form class="end">
    <label for="rua">Rua</label>
    <input type="text" v-model="endereco.logradouro" />
    <label for="num">Numero</label>
    <input type="text" v-model="endereco.numero" />
    <label for="bairro">Bairro</label>
    <input type="text" v-model="endereco.bairro" />
  </form>
  {{ endereco }}
</template>
<style>
  .end{
    display: flex;
    flex-direction: column;
  }
</style>
