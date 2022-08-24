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
  <main>
    <div>
      <h1>Calculadora de Gorjetas</h1>
      <div class="forms-gorjeta">
        <label for="">Qual o valor da conta?</label>
        <input type="number" v-model="valor" placeholder="0" />
      </div>
      <div class="forms-gorjeta">
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

      <div class="forms-gorjeta">
        <label for="">Quantas pessoas iram pagar?</label>
        <input type="number" v-model="pessoa" placeholder="1" />
      </div>

      <div>
        <h2>Valor da conta:</h2>
        <span>R$ {{ valor_final }} por pessoa</span>
      </div>
    </div>
  </main>
</template>
