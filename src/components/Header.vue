<template>
    <header>
      <div class="container-header">
        <h1>
          Calculadora
        </h1>
        <h5>Requisitos: Selects para os sinais matemáticos. <br> 2 displays para cada campo de operação</h5>
      </div>
    </header>
  </template>
  
  <style scoped>
  header {
    display: flex;
    justify-content: center;
  }
  
  .container-header {
    display: flex;
    flex-direction: column; 
    align-items: center; 
    color: #11183d;
    padding-bottom: 0;
  }
  .container-header h1 {
    margin: 0px;
    font-size: 44px;
  }

  .container-header h5 {
    margin-top: 0px;
    font-size: 12pxs;
  }
  </style>
  