<script setup>
import { reactive } from 'vue';
import Header from './components/Header.vue'
import Calc from './components/Calc.vue'

const estado = reactive({
  formula: '', // Armazenará a fórmula completa
  display1: '0', // Exibe o valor ou fórmula
  display2: '0', //exibe o valor ou fórmula do segundo display
  displayResultado: '0',
  operador: null
});

const atualizarDisplay = (valor) => {
  // Receber números iniciais
  if (estado.formula === '0' || estado.display1 === '0') {
    estado.formula = valor.toString();
    estado.display1 = estado.formula;
  } else if (!estado.operador && estado.formula !== '0') {
    estado.formula += valor.toString();
    estado.display1 = estado.formula;
  } else if (estado.operador) {
    // Adiciona o valor à segunda parte (após o operador)
    estado.formula += valor.toString();
    
    // Atualiza display2 com a parte após o operador
    const partes = estado.formula.split(estado.operador);
    estado.display2 = partes[1] || '';

  }

  estado.displayResultado = estado.formula;
};


const sinalMatematico = (sinal) => {
    estado.formula += sinal.toString();
    estado.displayResultado = estado.formula;
    estado.operador = sinal;
    return sinal;
}

const calcularResultado = () => {
  try {
    const resultado = eval(estado.formula); 
    estado.displayResultado = resultado.toString(); // Exibe o resultado no display
  } catch (error) {
    estado.displayResultado = 'Erro'; // Exibe "Erro" se a fórmula for inválida
    estado.formula = ''; // Limpa a fórmula para novo cálculo
  }
};


// Limpa tudo digitado ate o momento 
const limpaDisplay = () => {
    estado.formula = '0';
    estado.display1 = '0';
    estado.display2 = '0';
    estado.displayResultado = '0';
    estado.operador = '';
}

</script>

<template>
  <div class="container">
    <Header></Header>
    <Calc
      :atualizar-display="atualizarDisplay"
      :sinal-matematico="sinalMatematico"
      :calcular-resultado="calcularResultado"
      :limpa-display="limpaDisplay"
      :display1="estado.display1"
      :display2="estado.display2"
      :displayResultado="estado.displayResultado"
    />
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  display: block;
  width: 380px;
  max-width: 100%;
  height: 660px;
  background-color: #707fab8a;
  margin: 0 auto;
  border-radius: 15px;
  padding: 20px;
  margin-top: 18px;
}
</style>
