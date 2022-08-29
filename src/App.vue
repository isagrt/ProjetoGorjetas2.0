<script>
export default {
  data() {
    return {
      qualidades: [
        { qualidade: 5, servico: "Péssimo!" },
        { qualidade: 10, servico: "Ruim!" },
        { qualidade: 15, servico: "OK!" },
        { qualidade: 20, servico: "Bom!" },
        { qualidade: 25, servico: "Mais que bom!" },
        { qualidade: 30, servico: "Excelente!" },
      ],
      valor: 0,
      pessoa: 1,
      qualidade_selecionada: "",
    };
  },
  computed: {
    valor_final() {
      return (
        (this.valor * (1 + this.qualidade_selecionada / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>

<template>
  <main class="calculator">
    <div>
      <h1>Calculadora de Gorjetas</h1>
      <div class="formtip">
        <label for="">Qual o valor da conta?</label>
        <input type="number" v-model="valor" placeholder="0" />
      </div>
      <div class="formtip">
        <label for="select-servico">Como foi o serviço?</label>
        <select
          name="select-qualidade "
          id="select-servico"
          v-model="qualidade_selecionada"
        >
          <option disabled>Escolha um item</option>
          <option
            v-for="qualidade of qualidades"
            :key="qualidade.qualidade"
            for="select-servico"
            :value="qualidade.qualidade"
          >
            {{ qualidade.servico }}
          </option>
        </select>
      </div>

      <div class="formtip">
        <label for="">Quantas pessoas irão pagar?</label>
        <input type="number" v-model="pessoa" placeholder="1" />
      </div>
    </div>
  </main>
  <div class="result">
    <h2>Valor da conta:</h2>
    <span>R$ {{ valor_final }} por pessoa</span>
  </div>
</template>

<style>
h2 {
  font-size: 1.5em;
}
span {
  font-size: 2em;
}
body {
  margin: 0;
  padding: 0;
  font-family: "Lato", sans-serif;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
#app {
  display: flex;
}
.calculator {
  padding: 30px;
  border: 5px solid #636464;
}

.formtip {
  display: flex;
  flex-direction: column;
}
input,
select {
  padding: 2%;
  font-size: 1em;
}
label {
  font-size: 1.4em;
  padding: 1%;
}
.result {
  background-color: #636464;
  display: flex;
  /* padding: 7%; */
  border: 5px solid #636464;
  /* border-radius: 2%; */
  /* margin-top: 5%; */
  padding: 0 32px;
  align-items: center;
  justify-content: center;
}
</style>
