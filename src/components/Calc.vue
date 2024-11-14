<script setup>
const props = defineProps([
  'atualizarDisplay', 
  'sinalMatematico', 
  'calcularResultado', 
  'limpaDisplay',
  'display1', 
  'display2', 
  'displayResultado'
]);
</script>

<template>
  <section class="display">
    <input type="text" class="presenter" :value="props.display1" readonly />
    <input type="text" class="presenter" :value="props.display2" readonly />
    <input type="text" class="presenter" :value="props.displayResultado" readonly />
  </section>
  <section class="keyboard">
    <div class="line-1 lines">
      <button @click="props.atualizarDisplay(7)">7</button>
      <button @click="props.atualizarDisplay(8)">8</button>
      <button @click="props.atualizarDisplay(9)">9</button>
    </div>
    <div class="line-2 lines">
      <button @click="props.atualizarDisplay(4)">4</button>
      <button @click="props.atualizarDisplay(5)">5</button>
      <button @click="props.atualizarDisplay(6)">6</button>
    </div>
    <div class="line-3 lines">
      <button @click="props.atualizarDisplay(1)">1</button>
      <button @click="props.atualizarDisplay(2)">2</button>
      <button @click="props.atualizarDisplay(3)">3</button>
    </div>
    <div class="line-4 lines">
      <button @click="props.atualizarDisplay(0)">0</button>
      <button @click="props.atualizarDisplay('.')">,</button>
      <select @change="props.sinalMatematico($event.target.value)">
        <option disabled selected value>Operadores</option>
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="/">/</option>
        <option value="*">*</option>
      </select>
      <button @click="props.limpaDisplay()">Limpar</button>
      <button @click="props.calcularResultado()">Enter</button>
    </div>
  </section>
</template>

<style scoped>

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

.display1 {
  margin-top: 1px;
}
.presenter {
  background-color: #ffffff;
  height: 40px;
  border-radius: 8px;
  padding: 1%;
  padding-left: 40px;
  font-size: 40px;
  margin-bottom: 1%;
  width: calc(100% - 15%);
}

.keyboard {
  margin-top: 4%;
}
.lines {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 15px;
  margin-bottom: 15px;
}
.lines button {
  color: #15392cdf;
  height: 50px;
  font-size: 30px;
  border-radius: 15px;
}

</style>